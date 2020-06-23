---
title: Globální mezipaměť sestavení
description: Seznamte se s globální mezipamětí sestavení, která je mezipaměť kódu v celém počítači, kde je nainstalován modul CLR (Common Language Runtime) pro rozhraní .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
ms.openlocfilehash: 7f08bb4cf279924b12432f259dae8ce5a8474285
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104906"
---
# <a name="global-assembly-cache"></a>Globální mezipaměť sestavení
Každý počítač, ve kterém je nainstalován modul CLR (Common Language Runtime), má mezipaměť kódu v celém počítači nazývanou globální mezipaměť sestavení (GAC). Globální mezipaměť sestavení ukládá sestavení speciálně určená pro sdílení několika aplikacemi v počítači.  
  
 Sestavení byste měli sdílet tak, že je nainstalujete do globální mezipaměti sestavení (GAC) pouze v případě, že potřebujete. V rámci obecných pokynů, udržujte závislosti sestavení soukromě a vyhledejte sestavení v adresáři aplikace, pokud není explicitně požadováno sdílení sestavení. Kromě toho není nutné instalovat sestavení do globální mezipaměti sestavení (GAC), aby je bylo možné zpřístupnit pro zprostředkovatele komunikace s objekty COM nebo nespravovaný kód.  
  
> [!NOTE]
> Existují situace, kdy explicitně nechcete instalovat sestavení do globální mezipaměti sestavení (GAC). Pokud umístíte jedno ze sestavení, které tvoří aplikaci v globální mezipaměti sestavení (GAC), již nelze replikovat nebo nainstalovat aplikaci pomocí příkazu **xcopy** pro zkopírování adresáře aplikace. Je nutné přesunout sestavení také v globální mezipaměti sestavení (GAC).  
  
 Existují dva způsoby, jak nasadit sestavení do globální mezipaměti sestavení (GAC):  
  
- Použijte instalační program navržený pro práci s globální mezipamětí sestavení. Toto je upřednostňovaná možnost pro instalaci sestavení do globální mezipaměti sestavení (GAC).  
  
- Použijte vývojářský nástroj nazvaný [globální mezipaměť sestavení (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), který poskytuje Windows SDK.  
  
    > [!NOTE]
    > V rámci scénářů nasazení použijte Instalační služba systému Windows k instalaci sestavení do globální mezipaměti sestavení (GAC). Použijte nástroj globální mezipaměť sestavení (GAC) pouze ve scénářích vývoje, protože neposkytuje počítání odkazů na sestavení a další funkce, které jsou k dispozici při použití Instalační služba systému Windows.  
  
 Počínaje .NET Framework 4 je výchozí umístění pro globální mezipaměť sestavení **%windir%\Microsoft.NET\assembly**. V dřívějších verzích .NET Framework je výchozí umístění **%windir%\assembly**.  
  
 Správci často chrání adresář kořenová_složka_systému pomocí seznamu řízení přístupu (ACL) k řízení přístupu pro zápis a spouštění. Vzhledem k tomu, že je globální mezipaměť sestavení (GAC) nainstalovaná v podadresáři kořenové složky adresáře, zdědí seznam ACL tohoto adresáře. Doporučujeme, aby odstraňování souborů z globální mezipaměti sestavení bylo povoleno pouze uživatelům s oprávněními správce.  
  
 Sestavení nasazená v globální mezipaměti sestavení (GAC) musí mít silný název. Když je sestavení přidáno do globální mezipaměti sestavení (GAC), kontroly integrity se provádí na všech souborech, které tvoří sestavení. Mezipaměť provádí tyto kontroly integrity, aby bylo zajištěno, že sestavení nebylo manipulováno, například když došlo ke změně souboru, ale manifest neodráží změnu.  
  
## <a name="see-also"></a>Viz také

- [Sestavení v .NET](../../standard/assembly/index.md)
- [Práce se sestaveními a s globální pamětí sestavení](working-with-assemblies-and-the-gac.md)
- [Sestavení se silným názvem](../../standard/assembly/strong-named.md)
