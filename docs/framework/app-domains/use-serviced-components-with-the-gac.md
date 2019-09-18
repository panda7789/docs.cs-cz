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
ms.openlocfilehash: 4edc675e0348f06114b8162022f1d9420e0cec52
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053067"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Používání obsluhovaných komponent s globální pamětí sestavení
Obsluhované komponenty (komponenty modelu COM+ spravovaného kódu) by měly být vloženy do globální mezipaměti sestavení (GAC). V některých scénářích může modul CLR (Common Language Runtime) a služby COM+ zpracovávat obsluhované komponenty, které nejsou v globální mezipaměti sestavení (GAC). v jiných scénářích to nemůže. Tuto situaci ilustrují následující scénáře:  
  
- Pro obsluhované komponenty v serverové aplikaci modelu COM+ musí být sestavení obsahující komponenty v globální mezipaměti sestavení (GAC), protože Dllhost. exe neběží ve stejném adresáři jako ten, který obsahuje komponenty služby.  
  
- Pro obsluhované komponenty v knihovně COM+ mohou moduly runtime a COM+ vyřešit odkaz na sestavení obsahující komponenty hledáním v aktuálním adresáři. V takovém případě nemusí být sestavení v globální mezipaměti sestavení (GAC).  
  
- Pro obsluhované komponenty v aplikaci ASP.NET se situace liší. Pokud umístíte sestavení obsahující obsluhované komponenty do adresáře bin základní aplikace a použijete registraci na vyžádání, bude sestavení Stínově zkopírováno do mezipaměti pro stahování, protože ASP.NET využívá možnosti stínů modulu runtime.  
  
## <a name="see-also"></a>Viz také:

- [Práce se sestaveními a s globální pamětí sestavení](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (nástroj globální mezipaměti sestavení)](../tools/gacutil-exe-gac-tool.md)
