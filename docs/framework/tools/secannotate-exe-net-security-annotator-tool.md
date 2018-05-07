---
title: SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f4712970b2d3ebecf12cbb7b8f9b7fcdb317986
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)
Nástroj Security Annotator rozhraní .NET (SecAnnotate.exe) je aplikace příkazového řádku, který identifikuje `SecurityCritical` a `SecuritySafeCritical` části jeden nebo více sestavení.  
  
 Rozšíření sady Visual Studio, [popisování zabezpečení](http://go.microsoft.com/fwlink/?LinkId=198007), poskytuje grafické uživatelské rozhraní k SecAnnotate.exe a umožňuje spustit nástroj ze sady Visual Studio.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Na příkazovém řádku zadejte následující příkaz, kde *parametry* jsou popsané v následující části, a *sestavení* obsahovat jeden nebo více sestavení názvy oddělené mezerami:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/a`<br /><br /> or<br /><br /> `/showstatistics`|Zobrazí statistické údaje o použití průhlednosti v analyzovaných sestaveních.|  
|`/d:` *Adresář*<br /><br /> or<br /><br /> `/referencedir:` *Adresář*|Určuje adresář, ve kterém se mají hledat závislá sestavení během vytváření poznámek.|  
|`/i`<br /><br /> or<br /><br /> `/includesignatures`|Obsahuje rozšířené informace o podpisu v souboru zpráv poznámek.|  
|`/n`<br /><br /> or<br /><br /> `/nogac`|Potlačí vyhledávání odkazovaných sestavení v globální mezipaměti sestavení (GAC).|  
|`/o:` *output.XML*<br /><br /> or<br /><br /> `/out:` *output.XML*|Určuje název výstupního souboru poznámek.|  
|`/p:` *maxpasses*<br /><br /> or<br /><br /> `/maximumpasses:` *maxpasses*|Určuje maximální počet průchodů poznámek, které lze učinit na sestaveních před zastavením generování nových poznámek.|  
|`/q`<br /><br /> or<br /><br /> `/quiet`|Nastaví tichý režim, ve kterém nástroj pro tvorbu poznámek nevypisuje zprávy o stavu; vypisuje pouze chybové informace.|  
|`/r:` *Sestavení*<br /><br /> or<br /><br /> `/referenceassembly:` *Sestavení*|Při určování závislých sestavení během tvorby poznámek obsahuje zadané sestavení. Odkazovaná sestavení mají přednost před sestaveními, která jsou nalezena v zadané cestě odkazu.|  
|`/s:` *rulename*<br /><br /> or<br /><br /> `/suppressrule:` *rulename*|Potlačí spuštění zadaného pravidla průhlednosti na vstupních sestaveních.|  
|`/t`<br /><br /> or<br /><br /> `/forcetransparent`|Přinutí nástroj Annotator, aby považoval všechna sestavení, která nemají poznámky o průhlednosti, za zcela průhledná.|  
|`/t`:*sestavení*<br /><br /> or<br /><br /> `/forcetransparent`:*sestavení*|Vynutí průhlednost daného sestavení bez ohledu na aktuální poznámky na úrovni daného sestavení.|  
|||  
|`/v`<br /><br /> or<br /><br /> `/verify`|Pouze ověří, zda jsou poznámky sestavení správné; nepokusí se provést několik průchodů za účelem nalezení všech potřebných poznámek, není-li sestavení ověřeno.|  
|`/x`<br /><br /> or<br /><br /> `/verbose`|Určuje podrobný výstup při vytváření poznámek.|  
|`/y:` *Adresář*<br /><br /> or<br /><br /> `/symbolpath:` *Adresář*|Při vyhledávání souborů symbolů zahrne zadaný adresář během vytváření poznámek.|  
  
## <a name="remarks"></a>Poznámky  
 Parametry a sestavení mohou být rovněž poskytnuty v souboru odpovědí, který je zadán v příkazovém řádku a s předponou zavináč (@). Každý řádek v souboru odpovědí by měl obsahovat jediný parametr nebo název sestavení.  
  
 Další informace o popisování zabezpečení rozhraní .NET, naleznete v příspěvku [pomocí SecAnnotate analyzovat vaše sestavení pro průhlednost porušení](http://go.microsoft.com/fwlink/?LinkId=187648) v blogu zabezpečení rozhraní .NET.  
  
## <a name="examples"></a>Příklady
