---
title: Používání obsluhovaných komponent s globální pamětí sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a014058feb2ccb5187081fc63fb9c6eb6ac53d41
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607561"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Používání obsluhovaných komponent s globální pamětí sestavení
Obsluhované komponenty (spravované komponenty modelu COM +) měly být umístěny v globální mezipaměti sestavení. V některých scénářích modul Common Language Runtime a služby COM + zvládne obsluhované komponenty, které nejsou v globální mezipaměti sestavení; v jiných situacích možné. Následující scénáře popisují toto:  
  
- Obsluhované komponenty v aplikaci COM + Server sestavení obsahující komponenty musí být v globální mezipaměti sestavení, protože Dllhost.exe nejde spustit ve stejném adresáři jako ten, který obsahuje obsluhované komponenty.  
  
- Pro obsluhované komponenty v aplikaci knihovny modelu COM + modul runtime a služby COM + přeložit odkaz na sestavení obsahující komponenty tak, že v aktuálním adresáři. Sestavení v takovém případě nemusí být v globální mezipaměti sestavení.  
  
- Pro obsluhované komponenty v aplikaci ASP.NET se situace liší. Pokud umístíte sestavení obsahující obsluhované komponenty v adresáři bin základ cesty aplikace a používat na vyžádání registraci, bude sestavení stínové zkopírována do mezipaměti pro stahování vzhledem k tomu, že technologie ASP.NET využívá stínové možnosti modulu runtime.  
  
## <a name="see-also"></a>Viz také:

- [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
