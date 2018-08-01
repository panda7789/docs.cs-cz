---
title: Zapečetění
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f7202e10e41b9f114f42a4502ee2e6694bf3821
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573734"
---
# <a name="sealing"></a>Zapečetění
Jedna z funkcí objektově orientované rozhraní se vývojáři můžou rozšířit a přizpůsobit způsoby neočekávané návrháři framework. Toto je napájení i nebezpečí extensible návrhu. Při návrhu vaší framework je, proto velmi důležité pečlivě návrh pro rozšíření, pokud se požaduje a omezit rozšiřitelnosti, když je nebezpečné.  
  
 Zapečetění je výkonný mechanismus, který brání rozšíření. Můžete ji třídu nebo jednotlivé členy. Zapečetění třídu zabraňuje uživatelům v dědění ze třídy. Zapečetění členem zabraňuje uživatelům v přepsání konkrétní člena.  
  
 **X DO NOT** zapečetit třídy bez nutnosti důvodem k tomu.  
  
 Zapečetění třídu, protože nelze úvahách o scénářem rozšíření není dobrý důvod. Uživatelé Framework jako dědění ze třídy z různých důvodů nonobvious, například přidávání členů pohodlí. V tématu [Nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md) příklady nonobvious důvodů uživatelé chtějí dědit z typu.  
  
 Dobré důvody pro zapouzdření třídy zahrnují následující:  
  
-   Třída je statická třída. V tématu [statická třída návrhu](../../../docs/standard/design-guidelines/static-class.md).  
  
-   Třída ukládá tajné klíče citlivé na zabezpečení v zděděné chráněné členy.  
  
-   Třídy dědí mnoho členů virtuální a náklady na jejich jednotlivě zapečetění by převažují nad přínosy ponechání třídy nezapečetěné.  
  
-   Třída je atribut, který vyžaduje modul runtime velmi rychlé hledání. Zapečetěné atributů mají mírně vyšší úrovně výkonu než ty, které jsou nezapečetěné. v tématu [atributy](../../../docs/standard/design-guidelines/attributes.md).  
  
 **X DO NOT** deklarovat chráněný nebo virtuální členy v zapečetěných typech.  
  
 Podle definice nemůžou být zděděny zapečetěných typech. To znamená, že chráněné členy v zapečetěných typech nelze volat v zapečetěných typech virtuální metody nelze přepsat.  
  
 **✓ CONSIDER** zapečetění členů, které můžete přepsat.  
  
 Problémy, které může být důsledkem představení virtuální členové (popsané v [virtuální členové](../../../docs/standard/design-guidelines/virtual-members.md)) použít k přepsání i, i když mírně menší míře. Zapečetění přepsání chrání před tyto problémy od tohoto bodu v hierarchii dědičnosti.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md)
