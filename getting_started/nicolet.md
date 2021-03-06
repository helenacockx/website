---
title: Getting started with Nicolet data
tags: [nicolet, eeg, dataformat]
---

# Getting started with Nicolet data

Note: please add additional information if you have additional knowledge about Nicolet data that you want to share with other FieldTrip users.

## Introduction to the Nicolet file formats

The Nicolet system was once known as Nervus, launched in 1994/5 by Taugagreining in Iceland. This company was acquired by Viasys, then Carefusion, then Natus. Along the way the EEG system was renamed to Nicolet, then NicoletOne.

It is a popular clinical EEG format, especially in the Nordic countries.

The file format has been through some revisions. FieldTrip can read the file format from at least 2006 through 2018

- Files with the extension .e can be read in by FieldTrip 
- Older .eeg files probably have the same format with minor changes.

## Limits

The file format supports different sampling rates. Currently FieldTrip only reads the channels with the most popular sampling rate. This works well for clinical EEG.

## Integrations

This code also enables EEGLAB users to read the Nicolet file format through the FILEIO plugin in EEGLAB.

## Example

    nicoletfile = 'someNicoletFile.e';
    
    % using low-level functions
    hdr = ft_read_header(nicoletfile);
    data = ft_read_data(nicoletfile, 'header', hdr);

    % using high-level functions (recommended)
    cfg            = [];
    cfg.dataset    = nicoletfile;
    cfg.continuous = 'yes';
    cfg.channel    = 'all';
    data           = ft_preprocessing(cfg);

    cfg.viewmode   = 'vertical';
    ft_databrowser(cfg, data);

