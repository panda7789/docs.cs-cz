---
title: "Globální mezipaměť sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ca51a06e6e7ec89576facf3a70c789325fd893c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="global-assembly-cache"></a>Globální mezipaměť sestavení
Každý počítač, kde je nainstalován modul common language runtime má mezipaměť strojový kód volá globální mezipaměti sestavení. Globální mezipaměti sestavení uchovává sestavení konkrétně určená ke sdílení více aplikacemi v počítači.  
  
 Sestavení by měly sdílet instalací pouze v případě, že budete muset do globální mezipaměti sestavení. V rámci obecných pokynů udržujte sestavení závislosti privátním a vyhledání sestavení v adresáři aplikace, pokud sdílení sestavení není explicitně nutné. Kromě toho není nutné instalovat sestavení do globální mezipaměti sestavení do zpřístupněte je COM spolupráce nebo nespravovaného kódu.  
  
> [!NOTE]
>  Existují scénáře, kde explicitně nechcete instalovat sestavení do globální mezipaměti sestavení. Pokud jeden z těchto sestavení, které tvoří aplikaci v globální mezipaměti sestavení, můžete už replikovat nebo nainstalujte aplikaci pomocí **xcopy** příkaz pro kopírování adresáře aplikace. Je třeba přesunout sestavení v globální mezipaměti sestavení také.  
  
 Existují dva způsoby, jak nasazení sestavení do globální mezipaměti sestavení:  
  
-   Použijte instalační program navrženy pro práci s globální mezipaměti sestavení. Toto je upřednostňovaná možnost pro instalace sestavení do globální mezipaměti sestavení.  
  
-   Použijte nástroj vývojáře nazvaný [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), zadaný ve [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
    > [!NOTE]
    >  Ve scénářích nasazení použijte instalační služby systému Windows instalace sestavení do globální mezipaměti sestavení. Používejte nástroj globální mezipaměti sestavení jenom v situacích, vývoj, protože neposkytuje počítání odkazů sestavení a další funkce poskytované při použití Instalační služby systému Windows.  
  
 Od verze rozhraní .NET Framework 4, je výchozím umístěním pro globální mezipaměti sestavení **%windir%\Microsoft.NET\assembly**. V dřívějších verzích rozhraní .NET Framework, výchozím umístěním je **%windir%\assembly**.  
  
 Správci často chrání kořenovou složku pomocí seznam řízení přístupu (ACL) k řízení zápisu a provést přístup. Protože globální mezipaměti sestavení je nainstalována v podadresáři kořenového adresáře systému, dědí seznamu ACL tohoto adresáře. Doporučuje se, že mohou pouze uživatelé s oprávněním správce k odstranění souborů z globální mezipaměti sestavení.  
  
 Sestavení nasazené v globální mezipaměti sestavení musí mít silný název. Pokud je sestavení přidáno do globální mezipaměti sestavení, kontroly integrity se na všechny soubory, které tvoří sestavení. Mezipaměť provádí tyto kontroly integrity zajistit, že sestavení nikdo neoprávněně nemanipuloval, například když došlo ke změně souboru, ale manifest nezohledňuje změnu.  
  
## <a name="see-also"></a>Viz také  
 [Sestavení v modulu Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Práce se sestaveními a globální mezipaměti sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)
