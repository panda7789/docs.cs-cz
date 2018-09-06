---
title: Nezapečetěné třídy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef0f1c4c9b2d1928d6f96d62ab12df9786756498
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891374"
---
# <a name="unsealed-classes"></a>Nezapečetěné třídy
Zapečetěné třídy nelze dědit z, a brání tomu, aby rozšíření. Třídy, které je možné zdědit z naproti tomu se nazývají nezapečetěné třídy.  
  
 **✓ CONSIDER** použití nezapečetěných tříd bez přidat virtuální nebo chráněné členy, protože skvělý způsob, jak poskytnout nenákladné ještě mnohem vezme v úvahu rozšíření na rozhraní.  
  
 Vývojáři často má Zdědit z nezapečetěné třídy tak, aby přidat pohodlí členy jako jsou vlastní konstruktory, nové metody nebo přetížení metody. Například `System.Messaging.MessageQueue` nezapečetěná, a proto umožňuje uživatelům vytvářet vlastní fronty tuto výchozí hodnotu, do konkrétní fronty cesty nebo přidávání vlastních metod, které zjednodušují rozhraní API pro konkrétní scénáře.  
  
 Ve výchozím nastavení ve většině programovacích jazycích jsou nezapečetěné třídy a je také doporučené výchozí nastavení pro většinu tříd v rozhraní. Rozšiřitelnost poskytované nezapečetěné typy je ceníme uživatelé rozhraní framework a poměrně levné poskytnout kvůli relativně nízký testovací náklady spojené s nezapečetěné typy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Zapečetění](../../../docs/standard/design-guidelines/sealing.md)
