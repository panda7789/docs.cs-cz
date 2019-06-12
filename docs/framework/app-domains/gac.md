---
title: Globální mezipaměť sestavení
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 858d651523ac6196aa2dcad008ea53674eb01b04
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832844"
---
# <a name="global-assembly-cache"></a>Globální mezipaměť sestavení
Každý počítač, kde je nainstalován modul Common Language Runtime obsahuje mezipaměť kódu celého stroje názvem do globální mezipaměti sestavení. Global Assembly Cache ukládá sestavení speciálně určené ke sdílení více aplikacemi v počítači.  
  
 Sestavení by měly sdílet prostřednictvím instalace pouze v případě, že budete muset do globální mezipaměti sestavení. V rámci obecných pokynů udržujte soukromé závislosti sestavení a vyhledání sestavení v adresáři aplikace, pokud sdílení sestavení není explicitně vyžadováno. Kromě toho není nutné pro instalaci sestavení do globální mezipaměti sestavení zajistíte jejich přístupnost COM interop nebo nespravovaného kódu.  
  
> [!NOTE]
>  Existují scénáře, ve kterém můžete explicitně nechcete, aby instalace sestavení do globální mezipaměti sestavení. Pokud umístíte jednoho sestavení, které tvoří aplikaci v globální mezipaměti sestavení, můžete už replikovat nebo instalaci aplikace s použitím **xcopy** příkazu kopírování adresáře aplikace. Sestavení je nutné přesunout i globální mezipaměti sestavení.  
  
 Existují dva způsoby, jak nasadit sestavení do globální mezipaměti sestavení:  
  
- Pomocí instalačního programu navržené pro práci s globální pamětí sestavení. Toto je upřednostňovaná možnost pro instalaci sestavení do globální mezipaměti sestavení.  
  
- Použijte nástroj pro vývojáře, volá se, [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), k dispozici ve Windows Software Development Kit (SDK).  
  
    > [!NOTE]
    >  Ve scénářích nasazení použijte instalační služby systému Windows pro instalaci sestavení do globální mezipaměti sestavení. Použijte nástroj Global Assembly Cache pouze ve vývojové scénáře, protože neposkytuje počítání odkazů sestavení a další funkce, které poskytuje při použití Instalační služby systému Windows.  
  
 Od verze rozhraní .NET Framework 4, výchozím umístěním pro globální mezipaměť sestavení je **%windir%\Microsoft.NET\assembly**. V dřívějších verzích rozhraní .NET Framework, výchozí umístění je **%windir%\assembly**.  
  
 Správci často chrání pomocí seznam řízení přístupu (ACL) pro řízení zápisu a přístup pro spouštění kořenovou složku. Protože je nainstalována do globální mezipaměti sestavení v podadresáři kořenového adresáře dědí seznamu ACL tohoto adresáře. Doporučuje se, že pouze uživatelé s oprávněními správce bude moct odstranit soubory z globální mezipaměti sestavení.  
  
 Sestavení, které jsou nasazené v globální mezipaměti sestavení musí mít silný název. Pokud je sestavení přidáno do globální mezipaměti sestavení, kontroly integrity probíhají na všechny soubory, které tvoří sestavení. Mezipaměť provádí tyto kontroly integrity zajistit, že sestavení nebylo manipulováno, například když došlo ke změně souboru, ale manifest neodráží změny.  
  
## <a name="see-also"></a>Viz také:

- [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)
