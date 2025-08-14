# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is an educational repository for ENG 353L Poetry and AI, a course taught at Yale University during Fall 2024. The repository contains Jupyter notebook labs that explore the intersection of poetry and artificial intelligence through computational text analysis.

## Structure

- `Labs/` - Contains 5 Jupyter notebooks (DH Lab 1-5) that progressively build computational poetry analysis skills
- `README.md` - Basic repository description
- `Poetry_and_AI_Syllabus_Glaser.docx` - Course syllabus
- Various `.docx` files containing lab assignments and poetry exercises

## Working with Notebooks

All lab materials are Jupyter notebooks (.ipynb files) designed to run in Google Colab:

- Lab 1: Introduction to Python basics and text file handling
- Lab 2: Code tinkering with string manipulation and text analysis
- Lab 3: Word frequency analysis, shared word detection, and synonym generation
- Lab 4 & 5: More advanced computational poetry analysis

## Key Dependencies

The notebooks use standard Python libraries including:
- `collections.Counter` for word frequency analysis
- `re` (regex) for text preprocessing
- `nltk` and `wordnet` for natural language processing and synonym detection

## Development Notes

- No build, test, or lint commands - this is an educational repository with standalone notebooks
- Notebooks are intended to be run in Google Colab environment
- Students are expected to make copies to their own Google Drive before working
- Labs scale up in complexity and build on previous work
- Some advanced labs (enjambment, LLM training) are designed as group projects