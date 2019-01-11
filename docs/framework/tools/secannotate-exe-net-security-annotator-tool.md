---
title: SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be9100f49fcf6ed2926489e8346123eb7c3cfc70
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221346"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)
Nástroj .NET Security Annotator (SecAnnotate.exe) je aplikace příkazového řádku, který identifikuje `SecurityCritical` a `SecuritySafeCritical` části jedno nebo více sestavení.  
  
 Rozšíření sady Visual Studio [Security Annotator](https://go.microsoft.com/fwlink/?LinkId=198007), poskytuje grafické uživatelské rozhraní pro SecAnnotate.exe a umožňuje spouštět nástroj ze sady Visual Studio.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Na příkazovém řádku zadejte následující příkaz, kde *parametry* jsou popsány v následující části, a *sestavení* skládat z jednoho nebo více názvů sestavení oddělených mezerami:  
  
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
  
 Další informace o .NET Security Annotator naleznete v příspěvku [použití SecAnnotate k analýze sestavení narušení průhlednosti](https://go.microsoft.com/fwlink/?LinkId=187648) v blogu .NET Security.  
  
## <a name="examples"></a>Příklady
