---
title: "Nezapečetěné třídy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f950d8de2681868fe28e09e4b51bd8156cd12e94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unsealed-classes"></a>Nezapečetěné třídy
Zapečetěné třídy nelze zděděno z a zabraňují rozšíření. Třídy, které je možné zdědit z se nazývají naproti nezapečetěných třídy.  
  
 **✓ ZVAŽTE** použití nezapečetěných tříd bez přidat virtuální nebo chráněné členy, protože skvělý způsob, jak poskytnout nenákladné ještě mnohem vezme v úvahu rozšíření na rozhraní.  
  
 Vývojáři se často chtějí dědění z tříd nezapečetěných která přidat členy pohodlí například vlastní konstruktory, nové metody nebo přetížení metody. Například `System.Messaging.MessageQueue` nezapečetěná, a proto umožňuje uživatelům vytvářet vlastní fronty této výchozí do konkrétní fronty cesty, nebo při přidání vlastních metod, které zjednodušují rozhraní API pro konkrétní scénáře.  
  
 Třídy jsou nezapečetěné ve výchozím nastavení většina programovacích jazyků, který je taky doporučené výchozí nastavení pro Většina tříd v rozhraní. Rozšiřitelnost poskytované nezapečetěných typy je mnohem vezme v úvahu uživatelé framework a poměrně málo zajistit kvůli relativně nízký testovací náklady spojené s nezapečetěné typy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)  
 [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Zapečetění](../../../docs/standard/design-guidelines/sealing.md)
