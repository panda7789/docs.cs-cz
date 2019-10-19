---
title: Inherits – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: e92e12908c89bb7a0bf385a2122b0c8f1eb8a6f7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581758"
---
# <a name="inherits-statement"></a>Inherits – příkaz
Způsobí, že aktuální třída nebo rozhraní zdědí atributy, proměnné, vlastnosti, procedury a události z jiné třídy nebo sady rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`basetypenames`|Požadováno. Název třídy, ze které je tato třída odvozena.<br /><br /> -nebo-<br /><br /> Názvy rozhraní, ze kterých je toto rozhraní odvozeno. K oddělení více názvů použijte čárky.|  
  
## <a name="remarks"></a>Poznámky  
 V případě použití musí být příkaz `Inherits` prvním neprázdným řádkem bez komentářů v definici třídy nebo rozhraní. Měla by následovat bezprostředně po příkazu `Class` nebo `Interface`.  
  
 @No__t_0 lze použít pouze ve třídě nebo rozhraní. To znamená, že kontext deklarace pro dědičnost nemůže být zdrojový soubor, obor názvů, struktura, modul, procedura nebo blok.  
  
## <a name="rules"></a>Pravidly  
  
- **Dědičnost tříd.** Pokud třída používá příkaz `Inherits`, můžete zadat pouze jednu základní třídu.  
  
     Třída nemůže dědit z třídy, ve které je vnořená.  
  
- **Dědičnost rozhraní.** Pokud rozhraní používá příkaz `Inherits`, můžete zadat jedno nebo více základních rozhraní. Můžete Zdědit ze dvou rozhraní i v případě, že každý definuje člena se stejným názvem. Pokud to uděláte, implementace kódu musí použít kvalifikaci názvu k určení, který člen implementuje.  
  
     Rozhraní nemůže dědit z jiného rozhraní s více omezující úrovní přístupu. Rozhraní `Public` například nemůže dědit z rozhraní `Friend`.  
  
     Rozhraní nemůže dědit z rozhraní, které je v něm vnořené.  
  
 Příkladem dědičnosti třídy v .NET Framework je <xref:System.ArgumentException> třída, která dědí z třídy <xref:System.SystemException>. To umožňuje <xref:System.ArgumentException> všechny předdefinované vlastnosti a procedury vyžadované systémovými výjimkami, jako je například vlastnost <xref:System.Exception.Message%2A> a metoda <xref:System.Exception.ToString%2A>.  
  
 Příkladem dědičnosti rozhraní v .NET Framework je rozhraní <xref:System.Collections.ICollection>, které dědí z rozhraní <xref:System.Collections.IEnumerable>. To způsobí, <xref:System.Collections.ICollection> dědění definice výčtu potřebného k procházení kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Inherits` k zobrazení, jak třída s názvem `thisClass` může dědit všechny členy základní třídy s názvem `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dědění více rozhraní.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 Rozhraní s názvem `thisInterface` nyní zahrnuje všechny definice v rozhraních <xref:System.IComparable>, <xref:System.IDisposable> a <xref:System.IFormattable> zděděné členy v uvedeném pořadí pro porovnávání typů dvou objektů, uvolnění přidělených prostředků a vyjádření hodnoty objekt jako `String`. Třída, která implementuje `thisInterface` musí implementovat všechny členy každého základního rozhraní.  
  
## <a name="see-also"></a>Viz také:

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
