---
title: Inherits – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 5d88a01f90bc91a88229d19aa2368f8c71075b2f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404496"
---
# <a name="inherits-statement"></a>Inherits – příkaz
Způsobí, že aktuální třída nebo rozhraní zdědí atributy, proměnné, vlastnosti, procedury a události z jiné třídy nebo sady rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`basetypenames`|Povinná hodnota. Název třídy, ze které je tato třída odvozena.<br /><br /> -nebo-<br /><br /> Názvy rozhraní, ze kterých je toto rozhraní odvozeno. K oddělení více názvů použijte čárky.|  
  
## <a name="remarks"></a>Poznámky  
 Při použití `Inherits` musí být příkaz v definici třídy nebo rozhraní prvním neprázdným řádkem bez komentářů. Musí následovat po `Class` `Interface` příkazu nebo.  
  
 Můžete použít `Inherits` pouze v rámci třídy nebo rozhraní. To znamená, že kontext deklarace pro dědičnost nemůže být zdrojový soubor, obor názvů, struktura, modul, procedura nebo blok.  
  
## <a name="rules"></a>Pravidla  
  
- **Dědičnost tříd.** Pokud třída používá `Inherits` příkaz, můžete zadat pouze jednu základní třídu.  
  
     Třída nemůže dědit z třídy, ve které je vnořená.  
  
- **Dědičnost rozhraní.** Pokud rozhraní používá `Inherits` příkaz, můžete zadat jedno nebo více základních rozhraní. Můžete Zdědit ze dvou rozhraní i v případě, že každý definuje člena se stejným názvem. Pokud to uděláte, implementace kódu musí použít kvalifikaci názvu k určení, který člen implementuje.  
  
     Rozhraní nemůže dědit z jiného rozhraní s více omezující úrovní přístupu. `Public`Rozhraní nemůže například dědit z `Friend` rozhraní.  
  
     Rozhraní nemůže dědit z rozhraní, které je v něm vnořené.  
  
 Příkladem dědičnosti třídy v .NET Framework je <xref:System.ArgumentException> třída, která dědí z <xref:System.SystemException> třídy. To poskytuje <xref:System.ArgumentException> všechny předdefinované vlastnosti a procedury vyžadované systémovými výjimkami, jako je například <xref:System.Exception.Message%2A> vlastnost a <xref:System.Exception.ToString%2A> metoda.  
  
 Příkladem dědičnosti rozhraní v .NET Framework je <xref:System.Collections.ICollection> rozhraní, které dědí z <xref:System.Collections.IEnumerable> rozhraní. To způsobuje <xref:System.Collections.ICollection> dědění definice výčtu potřebného k procházení kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Inherits` příkaz k zobrazení, jak třída s názvem `thisClass` může dědit všechny členy základní třídy s názvem `anotherClass` .  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dědění více rozhraní.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 Rozhraní s názvem `thisInterface` nyní zahrnuje všechny definice v <xref:System.IComparable> <xref:System.IDisposable> <xref:System.IFormattable> rozhraních, a zděděné členy v uvedeném pořadí pro porovnávání typů dvou objektů, uvolnění přidělených prostředků a vyjádření hodnoty objektu jako `String` . Třída, která implementuje rozhraní, `thisInterface` musí implementovat všechny členy každého základního rozhraní.  
  
## <a name="see-also"></a>Viz také

- [MustInherit](../modifiers/mustinherit.md)
- [NotInheritable](../modifiers/notinheritable.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
- [Základní informace o dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Rozhraní](../../programming-guide/language-features/interfaces/index.md)
