---
title: SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)
description: Použijte SecAnnotate.exe Nástroj pro bezpečnostní anotaci .NET. Identifikujte SecurityCritical a SecuritySafeCritical části jednoho nebo více sestavení.
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
ms.openlocfilehash: 440ad39f1afb54ad517bc73f05d1e60748b7b520
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517214"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)
Nástroj bezpečnostní anotace .NET (SecAnnotate.exe) je aplikace příkazového řádku, která identifikuje `SecurityCritical` části a v `SecuritySafeCritical` jednom nebo více sestaveních.  
  
 Rozšíření sady Visual Studio, [bezpečnostní anotace](https://marketplace.visualstudio.com/items?itemName=sheldonb.SecurityAnnotator), poskytuje grafické uživatelské rozhraní pro SecAnnotate.exe a umožňuje spustit nástroj ze sady Visual Studio.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 Na příkazovém řádku zadejte následující příkaz, kde jsou *parametry* popsány v následující části a *sestavení* se skládají z jednoho nebo více názvů sestavení oddělených prázdnými znaky:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/a`<br /><br /> nebo<br /><br /> `/showstatistics`|Zobrazí statistické údaje o použití průhlednosti v analyzovaných sestaveních.|  
|`/d:`*adresář*<br /><br /> nebo<br /><br /> `/referencedir:`*adresář*|Určuje adresář, ve kterém se mají hledat závislá sestavení během vytváření poznámek.|  
|`/i`<br /><br /> nebo<br /><br /> `/includesignatures`|Obsahuje rozšířené informace o podpisu v souboru zpráv poznámek.|  
|`/n`<br /><br /> nebo<br /><br /> `/nogac`|Potlačí vyhledávání odkazovaných sestavení v globální mezipaměti sestavení (GAC).|  
|`/o:`*output.xml*<br /><br /> nebo<br /><br /> `/out:`*output.xml*|Určuje název výstupního souboru poznámek.|  
|`/p:`*maxpasses*<br /><br /> nebo<br /><br /> `/maximumpasses:`*maxpasses*|Určuje maximální počet průchodů poznámek, které lze učinit na sestaveních před zastavením generování nových poznámek.|  
|`/q`<br /><br /> nebo<br /><br /> `/quiet`|Nastaví tichý režim, ve kterém nástroj pro tvorbu poznámek nevypisuje zprávy o stavu; vypisuje pouze chybové informace.|  
|`/r:`*sestavení*<br /><br /> nebo<br /><br /> `/referenceassembly:`*sestavení*|Při určování závislých sestavení během tvorby poznámek obsahuje zadané sestavení. Odkazovaná sestavení mají přednost před sestaveními, která jsou nalezena v zadané cestě odkazu.|  
|`/s:`*Rule*<br /><br /> nebo<br /><br /> `/suppressrule:`*Rule*|Potlačí spuštění zadaného pravidla průhlednosti na vstupních sestaveních.|  
|`/t`<br /><br /> nebo<br /><br /> `/forcetransparent`|Přinutí nástroj Annotator, aby považoval všechna sestavení, která nemají poznámky o průhlednosti, za zcela průhledná.|  
|`/t`:*sestavení*<br /><br /> nebo<br /><br /> `/forcetransparent`:*sestavení*|Vynutí průhlednost daného sestavení bez ohledu na aktuální poznámky na úrovni daného sestavení.|  
|||  
|`/v`<br /><br /> nebo<br /><br /> `/verify`|Pouze ověří, zda jsou poznámky sestavení správné; nepokusí se provést několik průchodů za účelem nalezení všech potřebných poznámek, není-li sestavení ověřeno.|  
|`/x`<br /><br /> nebo<br /><br /> `/verbose`|Určuje podrobný výstup při vytváření poznámek.|  
|`/y:`*adresář*<br /><br /> nebo<br /><br /> `/symbolpath:`*adresář*|Při vyhledávání souborů symbolů zahrne zadaný adresář během vytváření poznámek.|  
  
## <a name="remarks"></a>Poznámky  
 Parametry a sestavení mohou být rovněž poskytnuty v souboru odpovědí, který je zadán v příkazovém řádku a s předponou zavináč (@). Každý řádek v souboru odpovědí by měl obsahovat jediný parametr nebo název sestavení.  
  
 Další informace o nástroji .NET Security anotace najdete v záznamu [pomocí SecAnnotate k analýze vašich sestavení pro porušení transparentnosti](https://docs.microsoft.com/archive/blogs/shawnfa/using-secannotate-to-analyze-your-assemblies-for-transparency-violations-an-example) na blogu zabezpečení .NET.  
  
## <a name="examples"></a>Příklady
