---
title: Návrh struktury
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: 8841a30f1dd0420b2ea45740b1e33bde5199c3f9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709046"
---
# <a name="struct-design"></a>Návrh struktury
Typ hodnoty pro obecné účely se nejčastěji označuje jako struktura a její C# klíčové slovo. V této části najdete pokyny pro obecný návrh struktury.  
  
 **X** neposkytuje konstruktor bez parametrů pro strukturu.  
  
 Podle těchto pokynů umožňuje vytvořit pole struktur bez nutnosti spuštění konstruktoru pro každou položku pole. Všimněte si C# , že neumožňuje strukturám mít konstruktory bez parametrů.  
  
 **X DO NOT** definování typů měnitelný hodnotu.  
  
 Proměnlivé typy hodnot mají několik problémů. Například pokud vlastnost getter vrátí typ hodnoty, volající obdrží kopii. Vzhledem k tomu, že kopie je vytvořena implicitně, vývojáři nemusí vědět, že se jedná o kopii, a nikoli původní hodnotu. Také některé jazyky (například dynamické jazyky) mají problémy s použitím proměnlivých hodnotových typů, protože i místní proměnné, pokud jsou převedené, způsobují vytvoření kopie.  
  
 **✓ DO** jistotu, že stav, kde všechny instance dat je nastavený na nulu, false, nebo hodnotu null (podle potřeby) je platný.  
  
 To brání nechtěnému vytvoření neplatných instancí při vytvoření pole struktury.  
  
 **✓ DO** implementovat <xref:System.IEquatable%601> u typů hodnot.  
  
 Metoda <xref:System.Object.Equals%2A?displayProperty=nameWithType> na hodnotových typech způsobuje zabalení a její výchozí implementace není velmi efektivní, protože používá reflexi. <xref:System.IEquatable%601.Equals%2A> může mít mnohem lepší výkon a může být implementováno tak, že nebude způsobovat zabalení.  
  
 **X DO NOT** explicitně rozšířit <xref:System.ValueType>. Většinou tyto jazyky tuto skutečnost znemožňují.  
  
 Obecně mohou být struktury velmi užitečné, ale měly by být použity pouze pro malé, jednoduché, neměnné hodnoty, které nebudou často zabaleny.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Volba mezi třídou a strukturou](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
