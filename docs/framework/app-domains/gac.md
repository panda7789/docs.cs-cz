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
ms.openlocfilehash: 3667a644253ab52d8421a1d4222e0bf8c03624c1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="global-assembly-cache"></a>Globální mezipaměť sestavení
Každý počítač, kde je nainstalován modul Common Language Runtime má mezipaměť strojový kód volá do globální mezipaměti sestavení. Globální mezipaměť sestavení uchovává sestavení konkrétně určená ke sdílení více aplikacemi v počítači.  
  
 Sestavení by měly sdílet instalací pouze v případě, že budete muset do globální mezipaměti sestavení. V rámci obecných pokynů udržujte sestavení závislosti privátním a vyhledání sestavení v adresáři aplikace, pokud sdílení sestavení není explicitně nutné. Kromě toho není nutné instalovat sestavení do globální mezipaměti sestavení tak, aby byly přístupné COM spolupráce nebo nespravovaného kódu.  
  
> [!NOTE]
>  Existují scénáře, kde explicitně nechcete instalovat sestavení do globální mezipaměti sestavení. Pokud jeden z těchto sestavení, které tvoří aplikaci v globální mezipaměti sestavení, můžete už replikovat nebo nainstalujte aplikaci pomocí **xcopy** příkaz pro kopírování adresáře aplikace. Je třeba přesunout sestavení do globální mezipaměti sestavení také.  
  
 Existují dva způsoby, jak nasazení sestavení do globální mezipaměti sestavení:  
  
-   Použijte instalační program navrženy pro práci s globální mezipaměti sestavení. Toto je upřednostňovaná možnost pro instalace sestavení do globální mezipaměti sestavení.  
  
-   Použijte nástroj vývojáře nazvaný [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), zadaný ve [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
    > [!NOTE]
    >  Ve scénářích nasazení použijte instalační služby systému Windows instalace sestavení do globální mezipaměti sestavení. Používejte nástroj globální mezipaměti sestavení jenom v situacích, vývoj, protože neposkytuje počítání odkazů sestavení a další funkce poskytované při použití Instalační služby systému Windows.  
  
 Od verze rozhraní .NET Framework 4, je výchozím umístěním pro globální mezipaměti sestavení **%windir%\Microsoft.NET\assembly**. V dřívějších verzích rozhraní .NET Framework, výchozím umístěním je **%windir%\assembly**.  
  
 Správci často chrání kořenovou složku pomocí seznam řízení přístupu (ACL) k řízení zápisu a provést přístup. Protože do globální mezipaměti sestavení je nainstalován v podadresáři kořenového adresáře systému, dědí seznamu ACL tohoto adresáře. Doporučuje se, že mohou pouze uživatelé s oprávněním správce k odstranění souborů z globální mezipaměti sestavení.  
  
 Sestavení nasazené v globální mezipaměti sestavení musí mít silný název. Pokud je sestavení přidáno do globální mezipaměti sestavení, kontroly integrity se na všechny soubory, které tvoří sestavení. Mezipaměť provádí tyto kontroly integrity zajistit, že sestavení nikdo neoprávněně nemanipuloval, například když došlo ke změně souboru, ale manifest nezohledňuje změnu.  
  
## <a name="see-also"></a>Viz také  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)
