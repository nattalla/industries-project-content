# CLAUDE.MD - Industries Project Content

## Project Overview

This repository contains industry and sector-specific content for a website project. The content is organized by major industry categories, with each containing detailed sector pages in markdown format.

## Project Structure

```
industries-project-content/
├── Consumer-Products/           # Consumer products industry sectors
├── Financial-Insurance-Services/ # Financial and insurance sectors
├── Logistics-Transportation/    # Logistics and transportation sectors
├── Manufacturing/               # Manufacturing industry sectors
├── Private-Capital/             # Private capital and investment sectors
├── Technology/                  # Technology sector content
├── ACF exports/                 # Advanced Custom Fields exports and backups
└── all media/                   # Centralized media files for all content
```

## Industry Categories

### 1. Consumer Products
Contains sector pages for:
- Apparel and Footwear
- Consumer Electronics
- Food and Beverage
- Household Goods
- Personal Care and Beauty
- Sporting Goods and Outdoor Equipment

### 2. Financial & Insurance Services
Contains sector pages for:
- Credit & Lending
- Financial Advisory
- Insurance Technology
- Reinsurance

Includes a `docx files/` subfolder with Word document versions.

### 3. Logistics & Transportation
Organized with:
- `parent-page/` - Master parent page content and sources
- `sectors/` - Individual sector content including:
  - Transportation
  - Supply Chain Management & Technology
  - Warehousing & Storage
- `Prototype/` - Prototype content and templates

### 4. Manufacturing
Contains sector pages for:
- Aerospace & Defense Manufacturing
- Automotive Manufacturing
- Chemical Manufacturing
- Consumer Goods Manufacturing
- Food & Beverage Manufacturing
- Industrial Equipment & Machinery Manufacturing

### 5. Private Capital
Contains sector pages for:
- Growth Equity
- Infrastructure Funds
- Private Credit
- Private Equity Buyout Firms
- Real Estate Private Equity
- Venture Capital

### 6. Technology
Technology sector-specific content.

## Content Organization

### File Naming Conventions
- Sector pages use snake_case: `Sector_Name_Sector_Page.md`
- Some sectors have multiple versions:
  - `_CONDENSED.md` - Condensed versions
  - `_UPDATED_DEC2025.md` - Recent updates with timestamps
  - `EDITTEMP` prefix - Temporary editing versions

### Content Format
- All content is in **Markdown** format (`.md` files)
- Some folders include `.docx` versions in subfolders
- Content is structured for WordPress/CMS integration

## Media Files

The `all media/` folder contains all images, videos, and other media assets referenced across the sector pages. This centralized approach ensures:
- No duplicate media files
- Easier media management
- Consistent asset references

## ACF Exports

The `ACF exports/` folder contains:
- Advanced Custom Fields configuration exports
- Backup files
- Field group updates

These are used for WordPress custom field configuration.

## Working with This Content

### Reading Content
- Start with the parent industry folder to understand the category
- Each sector page is self-contained with comprehensive information
- Check for `_CONDENSED` versions for quick overviews
- Look for timestamp suffixes for the most recent versions

### Adding New Content
1. Navigate to the appropriate industry folder
2. Follow existing naming conventions
3. Use markdown format
4. Place media files in `all media/` folder
5. Reference media using relative paths

### Editing Content
- Look for `EDITTEMP` versions if they exist (work in progress)
- Update version suffixes with current dates when making major changes
- Maintain consistent formatting with existing sector pages

## Git Workflow

- Main development branch: `claude/update-claude-md-ZFanK`
- Commit changes with descriptive messages
- Push to origin with: `git push -u origin claude/update-claude-md-ZFanK`

## Key Notes

- Content is designed for CMS/WordPress integration
- Each sector page follows a similar structure for consistency
- The project separates content (markdown) from media (centralized folder)
- Multiple versions of files may exist during editing process
- ACF exports are critical for maintaining custom field structure

## Content Structure Pattern

Most sector pages follow this general pattern:
1. Introduction and overview
2. Market dynamics and trends
3. Key challenges and opportunities
4. Industry-specific insights
5. Future outlook
6. Relevant statistics and data points

This structure ensures consistency across all industry and sector content.
