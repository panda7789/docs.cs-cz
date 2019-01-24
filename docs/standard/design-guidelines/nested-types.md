---
title: Vnořené typy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
author: KrzysztofCwalina
ms.openlocfilehash: 22c14d05105154ff642cb8a44eda8e7c5d0575e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559538"
---
# <a name="nested-types"></a>Vnořené typy
Vnořený typ je typ definovaný v rámci jiného typu, která se nazývá nadřazeného typu. Vnořený typ má přístup na všechny členy jeho nadřazeného typu. Například má přístup k privátním položkám definované nadřazeného typu a chráněné pole definovaná ve všech nadřazených členů nadřazeného typu.  
  
 Obecně platí vnořené typy by měly používat střídmě. Existuje několik důvodů. Někteří vývojáři nejsou plně seznámení s konceptem. Tyto vývojáře, například mít problémy se syntaxí File://Server.Fabrikam.com/SD deklarování proměnných vnořené typy. Vnořené typy jsou také velmi úzce svázány s jejich nadřazené typy a jako taková nejsou vhodné být obecné typy.  
  
 Vnořené typy jsou nejvhodnější pro modelování podrobnosti implementace jejich nadřazené typy. Koncový uživatel by měl mít jen zřídka pro deklarování proměnných vnořeného typu a téměř nikdy by měl mít explicitně vytvořit instanci vnořené typy. Například čítače výčtu kolekce může být vnořený typ této kolekce. Instance čítače se obvykle vytvářejí pomocí jejich nadřazených typů a protože mnoho jazyky podporují příkaz foreach, enumerátor proměnné zřídka musí deklarovat koncovým uživatelem.  
  
 **✓ DO** použití vnořené typy vztah mezi vnořené typy a jeho vnější typ tak, aby člen usnadnění sémantika je žádoucí.  
  
 **X DO NOT** použití veřejného vnořené typy jako logické seskupení vytvořit; pomocí oborů názvů pro tuto.  
  
 **X AVOID** veřejně vystaven vnořené typy. Jedinou výjimkou je, pokud proměnné vnořeného typu potřeba deklarovat pouze ve výjimečných případech, jako je například vytvoření podtřídy nebo jiné scénáře rozšířená přizpůsobení.  
  
 **X DO NOT** použijte vnořené typy, pokud typ je pravděpodobně bude odkazovat mimo nadřazeného typu.  
  
 Například výčet předaný metodě definované třídy nesmí být definována jako vnořený typ ve třídě.  
  
 **X DO NOT** použít vnořené typy, pokud je nutné vytvořit instanci kódem na straně klienta.  Pokud typ nemá veřejný konstruktor, ji by měl pravděpodobně není vnořit.  
  
 Pokud můžete vytvořit instanci typu, který zdá se, že označuje typ má místo v rámci sama o sobě (můžete ji vytvořit, pracujete s ním a zničit bez někdy použití vnějšího typu) a proto by neměl být vnořený. Vnitřní typy by neměly znovu použít široce mimo vnější typ bez jakékoli relace jednání do vnějšího typu.  
  
 **X DO NOT** definovat vnořené typy jako člen rozhraní. Řadu jiných jazyků nepodporují tato konstrukce.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
