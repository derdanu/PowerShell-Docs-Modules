---
external help file: platyPS-help.xml
Module Name: platyPS
ms.date: 03/16/2021
online version: https://learn.microsoft.com/powershell/module/platyps/new-externalhelpcab?view=ps-modules&wt.mc_id=ps-gethelp
schema: 2.0.0
---

# New-ExternalHelpCab

## SYNOPSIS
Generates a `.cab` file.

## SYNTAX

```
New-ExternalHelpCab -CabFilesFolder <String> -LandingPagePath <String>
 -OutputFolder <String>
 [-IncrementHelpVersion] [<CommonParameters>]
```

## DESCRIPTION

The `New-ExternalHelpCab` cmdlet generates a `.cab` file that contains all the non-recursive content
in a folder. This cmdlet compresses the provided files.

> [!NOTE]
> This cmdlet depends on the `MakeCab.exe` native command, which is only available on Windows. This
> cmdlet raises an error if used on non-Windows machines.

We recommend that you provide as content only about_ topics and the output from the
[New-ExternalHelp](New-ExternalHelp.md) cmdlet to this cmdlet.

This cmdlet uses metadata stored in the module markdown file to name your `.cab` file. This naming
matches the pattern that the PowerShell help system requires for use as updatable help. This
metadata is part of the module file created using the [New-MarkdownHelp](New-MarkdownHelp.md)
cmdlet with the **WithModulePage** parameter.

This cmdlet also generates or updates an existing `helpinfo.xml` file. That file provides versioning
and locale details to the PowerShell help system.

## EXAMPLES

### Example 1: Create a CAB file

```powershell
$params = @{
    CabFilesFolder  = 'C:\Module\ExternalHelpContent'
    LandingPagePath = 'C:\Module\ModuleName.md'
    OutputFolder    = 'C:\Module\Cab\'
}
New-ExternalHelpCab @params
```

The cmdlet creates a `.cab` file that contains the content folder files. The `.cab` file is named
for updatable help based on metadata. The command places the `.cab` file in the output folder.

## PARAMETERS

### -CabFilesFolder

Specifies the folder that contains the help content that this cmdlet packages into a `.cab` file.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LandingPagePath

Specifies the full path of the module Markdown file that contains all the metadata required to name
the `.cab` file. For the required metadata, run `New-MarkdownHelp` with the **WithLandingPage**
parameter.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputFolder

Specifies the location of the `.cab` file and `helpinfo.xml` file that this cmdlet creates.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncrementHelpVersion

Automatically increment the help version in the module Markdown file.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable,
-InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose,
-WarningAction, and -WarningVariable. For more information, see
[about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

You can't pipe values to this cmdlet.

## OUTPUTS

### None

This cmdlet doesn't generate output. The cmdlet saves its results in the output folder that the
**OutputPath** parameter specifies.

## NOTES

## RELATED LINKS

[New-ExternalHelp](New-ExternalHelp.md)
[New-MarkdownAboutHelp](New-MarkdownAboutHelp.md)
