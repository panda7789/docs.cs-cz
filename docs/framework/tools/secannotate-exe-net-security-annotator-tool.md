---
title: SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
ms.openlocfilehash: cc57bd01c5626c889b5d94eac1e7358cafa4ab10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447319"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)
The .NET Security Annotator tool (SecAnnotate.exe) is a command-line application that identifies the `SecurityCritical` and `SecuritySafeCritical` portions of one or more assemblies.  
  
 A Visual Studio extension, [Security Annotator](https://marketplace.visualstudio.com/items?itemName=sheldonb.SecurityAnnotator), provides a graphical user interface to SecAnnotate.exe and enables you to run the tool from Visual Studio.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). For more information, see [Command Prompts](developer-command-prompt-for-vs.md).  
  
 At the command prompt, type the following, where *parameters* are described in the following section, and *assemblies* consist of one or more assembly names separated by blanks:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/a`<br /><br /> or<br /><br /> `/showstatistics`|Zobrazí statistické údaje o použití průhlednosti v analyzovaných sestaveních.|  
|`/d:` *directory*<br /><br /> or<br /><br /> `/referencedir:` *directory*|Určuje adresář, ve kterém se mají hledat závislá sestavení během vytváření poznámek.|  
|`/i`<br /><br /> or<br /><br /> `/includesignatures`|Obsahuje rozšířené informace o podpisu v souboru zpráv poznámek.|  
|`/n`<br /><br /> or<br /><br /> `/nogac`|Potlačí vyhledávání odkazovaných sestavení v globální mezipaměti sestavení (GAC).|  
|`/o:` *output.xml*<br /><br /> or<br /><br /> `/out:` *output.xml*|Určuje název výstupního souboru poznámek.|  
|`/p:` *maxpasses*<br /><br /> or<br /><br /> `/maximumpasses:` *maxpasses*|Určuje maximální počet průchodů poznámek, které lze učinit na sestaveních před zastavením generování nových poznámek.|  
|`/q`<br /><br /> or<br /><br /> `/quiet`|Nastaví tichý režim, ve kterém nástroj pro tvorbu poznámek nevypisuje zprávy o stavu; vypisuje pouze chybové informace.|  
|`/r:` *assembly*<br /><br /> or<br /><br /> `/referenceassembly:` *assembly*|Při určování závislých sestavení během tvorby poznámek obsahuje zadané sestavení. Odkazovaná sestavení mají přednost před sestaveními, která jsou nalezena v zadané cestě odkazu.|  
|`/s:` *rulename*<br /><br /> or<br /><br /> `/suppressrule:` *rulename*|Potlačí spuštění zadaného pravidla průhlednosti na vstupních sestaveních.|  
|`/t`<br /><br /> or<br /><br /> `/forcetransparent`|Přinutí nástroj Annotator, aby považoval všechna sestavení, která nemají poznámky o průhlednosti, za zcela průhledná.|  
|`/t`:*assembly*<br /><br /> or<br /><br /> `/forcetransparent`:*assembly*|Vynutí průhlednost daného sestavení bez ohledu na aktuální poznámky na úrovni daného sestavení.|  
|||  
|`/v`<br /><br /> or<br /><br /> `/verify`|Pouze ověří, zda jsou poznámky sestavení správné; nepokusí se provést několik průchodů za účelem nalezení všech potřebných poznámek, není-li sestavení ověřeno.|  
|`/x`<br /><br /> or<br /><br /> `/verbose`|Určuje podrobný výstup při vytváření poznámek.|  
|`/y:` *directory*<br /><br /> or<br /><br /> `/symbolpath:` *directory*|Při vyhledávání souborů symbolů zahrne zadaný adresář během vytváření poznámek.|  
  
## <a name="remarks"></a>Poznámky  
 Parametry a sestavení mohou být rovněž poskytnuty v souboru odpovědí, který je zadán v příkazovém řádku a s předponou zavináč (@). Každý řádek v souboru odpovědí by měl obsahovat jediný parametr nebo název sestavení.  
  
 For more information about the .NET Security Annotator, see the entry [Using SecAnnotate to Analyze Your Assemblies for Transparency Violations](https://blogs.msdn.microsoft.com/shawnfa/2009/11/18/using-secannotate-to-analyze-your-assemblies-for-transparency-violations-an-example/) in the .NET Security blog.  
  
## <a name="examples"></a>Příklady
