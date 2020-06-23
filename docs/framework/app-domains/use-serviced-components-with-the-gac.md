---
title: Používání obsluhovaných komponent s globální pamětí sestavení
description: Použití obsluhované komponenty (komponenty modelu COM+ spravovaného kódu) s globální mezipamětí sestavení v .NET. Podívejte se, zda CLR a služby COM+ mohou zpracovávat komponenty, které nejsou součástí GAC.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
ms.openlocfilehash: 6b7371865b7b1cedda0ee03b2cc28c74b5c3da0b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104478"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Používání obsluhovaných komponent s globální pamětí sestavení
Obsluhované komponenty (komponenty modelu COM+ spravovaného kódu) by měly být vloženy do globální mezipaměti sestavení (GAC). V některých scénářích může modul CLR (Common Language Runtime) a služby COM+ zpracovávat obsluhované komponenty, které nejsou v globální mezipaměti sestavení (GAC). v jiných scénářích to nemůže. Tuto situaci ilustrují následující scénáře:  
  
- Pro obsluhované komponenty v serverové aplikaci COM+ musí být sestavení obsahující komponenty v globální mezipaměti sestavení (GAC), protože Dllhost.exe neběží ve stejném adresáři jako ten, který obsahuje komponenty služby.  
  
- Pro obsluhované komponenty v knihovně COM+ mohou moduly runtime a COM+ vyřešit odkaz na sestavení obsahující komponenty hledáním v aktuálním adresáři. V takovém případě nemusí být sestavení v globální mezipaměti sestavení (GAC).  
  
- Pro obsluhované komponenty v aplikaci ASP.NET se situace liší. Pokud umístíte sestavení obsahující obsluhované komponenty do adresáře bin základní aplikace a použijete registraci na vyžádání, bude sestavení Stínově zkopírováno do mezipaměti pro stahování, protože ASP.NET využívá možnosti stínů modulu runtime.  
  
## <a name="see-also"></a>Viz také

- [Práce se sestaveními a s globální pamětí sestavení](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
