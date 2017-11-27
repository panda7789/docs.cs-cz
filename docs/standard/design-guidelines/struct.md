---
title: "Struktura návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1566d2b67e1dda5b0b221a2c10affb6bdaea888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="struct-design"></a>Struktura návrhu
Typ hodnoty pro obecné účely se nejčastěji označuje jako struktury, jeho C# – klíčové slovo. Tato část obsahuje pokyny pro návrh obecná struktura.  
  
 **X nesmí** zadejte výchozí konstruktor pro struktury.  
  
 Následující obecné této zásady umožňuje pole struktur, který se má vytvořit bez nutnosti spuštění konstruktoru na každou položku pole. Všimněte si, že C# neumožňuje struktury tak, aby měl výchozí konstruktory.  
  
 **X nesmí** definování typů měnitelný hodnotu.  
  
 Typy hodnot měnitelný mít několik problémů. Například v případě, že metoda getter vlastnosti vrátí typ hodnoty, volající obdrží kopii. Protože kopie je vytvořena implicitně, nemusíte být vědomi, mutace kopií a není původní hodnota vývojáři. Některé jazyky (dynamické jazyky konkrétně) také mít problémy pomocí typy měnitelný hodnot, protože dokonce i místní proměnné, když vyhodnoceny odkazy, způsobit kopie má být provedeno.  
  
 **PROVEĎTE ✓** jistotu, že stav, kde všechny instance dat je nastavený na nulu, false, nebo hodnotu null (podle potřeby) je platný.  
  
 Při vytváření pole struktury zabrání náhodnému vytváření instancí neplatný.  
  
 **PROVEĎTE ✓** implementovat <xref:System.IEquatable%601> u typů hodnot.  
  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType> Metoda u typů hodnot způsobí, že zabalení a jeho výchozí implementace není velmi efektivní, protože používá reflexe. <xref:System.IEquatable%601.Equals%2A>může mít mnohem lepší výkon a může být implementováno tak, aby nezpůsobí zabalení.  
  
 **X nesmí** explicitně rozšířit <xref:System.ValueType>. Většina jazyků zabránit ve skutečnosti to.  
  
 Obecně platí struktury může být velmi užitečná, ale musí být použit pouze pro malé, jeden, neměnné hodnoty, které nebudou často do pole.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Typ pokynů pro návrh](../../../docs/standard/design-guidelines/type.md)  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)  
 [Volba mezi třídy a struktury](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
