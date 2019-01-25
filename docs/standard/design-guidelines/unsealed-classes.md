---
title: Nezapečetěné třídy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: d7174de7ddf062b829672e04952c1010fcb74058
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616927"
---
# <a name="unsealed-classes"></a>Nezapečetěné třídy
Zapečetěné třídy nelze dědit z, a brání tomu, aby rozšíření. Třídy, které je možné zdědit z naproti tomu se nazývají nezapečetěné třídy.  
  
 **✓ CONSIDER** použití nezapečetěných tříd bez přidat virtuální nebo chráněné členy, protože skvělý způsob, jak poskytnout nenákladné ještě mnohem vezme v úvahu rozšíření na rozhraní.  
  
 Vývojáři často má Zdědit z nezapečetěné třídy tak, aby přidat pohodlí členy jako jsou vlastní konstruktory, nové metody nebo přetížení metody. Například `System.Messaging.MessageQueue` nezapečetěná, a proto umožňuje uživatelům vytvářet vlastní fronty tuto výchozí hodnotu, do konkrétní fronty cesty nebo přidávání vlastních metod, které zjednodušují rozhraní API pro konkrétní scénáře.  
  
 Ve výchozím nastavení ve většině programovacích jazycích jsou nezapečetěné třídy a je také doporučené výchozí nastavení pro většinu tříd v rozhraní. Rozšiřitelnost poskytované nezapečetěné typy je ceníme uživatelé rozhraní framework a poměrně levné poskytnout kvůli relativně nízký testovací náklady spojené s nezapečetěné typy.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Zapečetění](../../../docs/standard/design-guidelines/sealing.md)
