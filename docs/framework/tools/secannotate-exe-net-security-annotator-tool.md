---
title: SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
ms.openlocfilehash: ffc275c588775fb79da276be904ada90a5a31bad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937931"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)
Nástroj anotátor .NET Security (SecAnnotate.exe) je aplikace příkazového `SecurityCritical` řádku, která identifikuje a `SecuritySafeCritical` části jednoho nebo více sestavení.  
  
 Rozšíření sady Visual Studio, [security annotator](https://marketplace.visualstudio.com/items?itemName=sheldonb.SecurityAnnotator), poskytuje grafické uživatelské rozhraní pro secAnnotate.exe a umožňuje spustit nástroj z aplikace Visual Studio.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 Na příkazovém řádku zadejte následující text, kde jsou *parametry popsány* v následující části a *sestavy* se skládají z jednoho nebo více názvů sestavení oddělených mezerami:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/a`<br /><br /> – nebo –<br /><br /> `/showstatistics`|Zobrazí statistické údaje o použití průhlednosti v analyzovaných sestaveních.|  
|`/d:`*adresář*<br /><br /> – nebo –<br /><br /> `/referencedir:`*adresář*|Určuje adresář, ve kterém se mají hledat závislá sestavení během vytváření poznámek.|  
|`/i`<br /><br /> – nebo –<br /><br /> `/includesignatures`|Obsahuje rozšířené informace o podpisu v souboru zpráv poznámek.|  
|`/n`<br /><br /> – nebo –<br /><br /> `/nogac`|Potlačí vyhledávání odkazovaných sestavení v globální mezipaměti sestavení (GAC).|  
|`/o:`*output.xml*<br /><br /> – nebo –<br /><br /> `/out:`*output.xml*|Určuje název výstupního souboru poznámek.|  
|`/p:`*maxpasses*<br /><br /> – nebo –<br /><br /> `/maximumpasses:`*maxpasses*|Určuje maximální počet průchodů poznámek, které lze učinit na sestaveních před zastavením generování nových poznámek.|  
|`/q`<br /><br /> – nebo –<br /><br /> `/quiet`|Nastaví tichý režim, ve kterém nástroj pro tvorbu poznámek nevypisuje zprávy o stavu; vypisuje pouze chybové informace.|  
|`/r:`*montáž*<br /><br /> – nebo –<br /><br /> `/referenceassembly:`*montáž*|Při určování závislých sestavení během tvorby poznámek obsahuje zadané sestavení. Odkazovaná sestavení mají přednost před sestaveními, která jsou nalezena v zadané cestě odkazu.|  
|`/s:`*název pravidla*<br /><br /> – nebo –<br /><br /> `/suppressrule:`*název pravidla*|Potlačí spuštění zadaného pravidla průhlednosti na vstupních sestaveních.|  
|`/t`<br /><br /> – nebo –<br /><br /> `/forcetransparent`|Přinutí nástroj Annotator, aby považoval všechna sestavení, která nemají poznámky o průhlednosti, za zcela průhledná.|  
|`/t`:*montáž*<br /><br /> – nebo –<br /><br /> `/forcetransparent`:*montáž*|Vynutí průhlednost daného sestavení bez ohledu na aktuální poznámky na úrovni daného sestavení.|  
|||  
|`/v`<br /><br /> – nebo –<br /><br /> `/verify`|Pouze ověří, zda jsou poznámky sestavení správné; nepokusí se provést několik průchodů za účelem nalezení všech potřebných poznámek, není-li sestavení ověřeno.|  
|`/x`<br /><br /> – nebo –<br /><br /> `/verbose`|Určuje podrobný výstup při vytváření poznámek.|  
|`/y:`*adresář*<br /><br /> – nebo –<br /><br /> `/symbolpath:`*adresář*|Při vyhledávání souborů symbolů zahrne zadaný adresář během vytváření poznámek.|  
  
## <a name="remarks"></a>Poznámky  
 Parametry a sestavení mohou být rovněž poskytnuty v souboru odpovědí, který je zadán v příkazovém řádku a s předponou zavináč (@). Každý řádek v souboru odpovědí by měl obsahovat jediný parametr nebo název sestavení.  
  
 Další informace o anotátoru zabezpečení .NET naleznete v položce [Using SecAnnotate to Analyze Your Assemblies for Transparency Violations](https://docs.microsoft.com/archive/blogs/shawnfa/using-secannotate-to-analyze-your-assemblies-for-transparency-violations-an-example) v blogu .NET Security.  
  
## <a name="examples"></a>Příklady
