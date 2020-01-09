---
title: Zapečetění
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: 0920ea26b94d86b41f8ba9338f3ec19f9bc099e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709085"
---
# <a name="sealing"></a>Zapečetění
Jednou z funkcí objektů orientovaných na objekty je, že je vývojáři mohou roztáhnout a přizpůsobit způsobem, který neočekává návrháři rozhraní. Jedná se o výkon i nebezpečí rozšiřitelného návrhu. Při návrhu architektury je proto velmi důležité pečlivě navrhovat rozšiřitelnost, když je to žádoucí, a omezit rozšiřitelnost, pokud je to nebezpečné.  
  
 Výkonný mechanismus, který brání rozšíření. Můžete zapečetit buď třídu, nebo jednotlivé členy. Zapečetění třídy brání uživatelům v dědění z třídy. Uzavření člena zabrání uživatelům v přepsání určitého člena.  
  
 **X DO NOT** zapečetit třídy bez nutnosti důvodem k tomu.  
  
 Zapečetění třídy, protože si nemůžete představit scénář rozšiřitelnosti není dobrým důvodem. Uživatelé rozhraní, jako je dědění z tříd pro různé Nezřejmé důvody, jako je přidání praktických členů. Příklady nezřejméch důvodů, které uživatelé chtějí zdědit z typu, naleznete v tématu [nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md) .  
  
 Mezi vhodné důvody pro zapečetění třídy patří následující:  
  
- Třída je statická třída. Viz [design statické třídy](../../../docs/standard/design-guidelines/static-class.md).  
  
- Třída ukládá tajné klíče citlivé na zabezpečení ve zděděných chráněných členech.  
  
- Třída zdědí mnoho virtuálních členů a náklady na jejich zapečetění, by převažují nad výhodami opustit třídu, která není zapečetěná.  
  
- Třída je atribut, který vyžaduje velmi rychlé vyhledání za běhu. Zapečetěné atributy mají mírně vyšší úroveň výkonu než nezapečetěné. viz [atributy](../../../docs/standard/design-guidelines/attributes.md).  
  
 **X DO NOT** deklarovat chráněný nebo virtuální členy v zapečetěných typech.  
  
 Podle definice nemůže být zapečetěné typy děděny. To znamená, že nelze volat chráněné členy pro zapečetěné typy a virtuální metody pro zapečetěné typy nelze přepsat.  
  
 **✓ CONSIDER** zapečetění členů, které můžete přepsat.  
  
 Problémy, které mohou vést k představení virtuálních členů (popsaných v tématu [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)), se vztahují i na přepsání, i když do mírně menšího stupně. Z tohoto okamžiku v hierarchii dědičnosti zapečetí přepisy, které z těchto problémů začínají.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Nezapečetěné třídy](../../../docs/standard/design-guidelines/unsealed-classes.md)
