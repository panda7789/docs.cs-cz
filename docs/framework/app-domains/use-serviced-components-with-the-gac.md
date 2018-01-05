---
title: "Používání obsluhovaných komponent s globální pamětí sestavení"
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
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb9bd85797dd129f6f34992c58c9772668ce2cb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Používání obsluhovaných komponent s globální pamětí sestavení
Obsluhované komponenty (spravované komponenty modelu COM +) měly být umístěny v globální mezipaměti sestavení. V některých scénářích modul Common Language Runtime a služby COM + může zpracovávat obsluhované komponenty, které nejsou v globální mezipaměti sestavení; v jiných scénářích nelze. Následující scénáře popisují toto:  
  
-   Obsluhované komponenty aplikace modelu COM + serveru sestavení obsahující komponenty musí být v globální mezipaměti sestavení, protože Dllhost.exe nejde spustit ve stejném adresáři jako ta, která obsahuje obsluhované komponenty.  
  
-   Pro obsluhované komponenty aplikace modelu COM + knihovny modulu runtime a služby COM + přeložit odkaz na sestavení obsahující komponenty pomocí vyhledávání v aktuálním adresáři. Sestavení v takovém případě nemusí být v globální mezipaměti sestavení.  
  
-   Obsluhované komponenty v aplikaci ASP.NET je různé situace. Pokud umístíte sestavení obsahující obsluhované komponenty v adresáři bin základu aplikace a použijete registrace na vyžádání, sestavení bude vytvořena stínová kopie mezipaměť pro stahování protože ASP.NET využívá možnosti stínové kopie modulu runtime.  
  
## <a name="see-also"></a>Viz také  
 [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
