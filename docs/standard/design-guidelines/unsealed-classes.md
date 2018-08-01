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
ms.openlocfilehash: 672d36c6b888ee9a89a76d5d417a7a7e92dd8f36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571658"
---
# <a name="unsealed-classes"></a>Nezapečetěné třídy
Zapečetěné třídy nelze zděděno z a zabraňují rozšíření. Třídy, které je možné zdědit z se nazývají naproti nezapečetěných třídy.  
  
 **✓ CONSIDER** použití nezapečetěných tříd bez přidat virtuální nebo chráněné členy, protože skvělý způsob, jak poskytnout nenákladné ještě mnohem vezme v úvahu rozšíření na rozhraní.  
  
 Vývojáři se často chtějí dědění z tříd nezapečetěných která přidat členy pohodlí například vlastní konstruktory, nové metody nebo přetížení metody. Například `System.Messaging.MessageQueue` nezapečetěná, a proto umožňuje uživatelům vytvářet vlastní fronty této výchozí do konkrétní fronty cesty, nebo při přidání vlastních metod, které zjednodušují rozhraní API pro konkrétní scénáře.  
  
 Třídy jsou nezapečetěné ve výchozím nastavení většina programovacích jazyků, který je taky doporučené výchozí nastavení pro Většina tříd v rozhraní. Rozšiřitelnost poskytované nezapečetěných typy je mnohem vezme v úvahu uživatelé framework a poměrně málo zajistit kvůli relativně nízký testovací náklady spojené s nezapečetěné typy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Zapečetění](../../../docs/standard/design-guidelines/sealing.md)
