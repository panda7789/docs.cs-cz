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
ms.openlocfilehash: 5ab90e44e2809c1e71d7f100970b7be73af4a732
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817094"
---
# <a name="inherits-statement"></a>Inherits – příkaz
Způsobí, že aktuální třída nebo rozhraní zdědí atributy, proměnné, vlastnosti, procedury a události z jiné třídy nebo sady rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`basetypenames`|Povinný parametr. Název třídy, ze kterého tato třída odvozená.<br /><br /> -nebo-<br /><br /> Názvy rozhraní, ze kterých tato rozhraní je odvozena. Použijte čárky k oddělení více názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud použijete, `Inherits` příkaz musí být na prvním řádku neprázdné, mimo komentář v definici třídy nebo rozhraní. Měla by odpovídat okamžitě `Class` nebo `Interface` příkazu.  
  
 Můžete použít `Inherits` pouze ve třídě nebo rozhraní. To znamená, že se že kontext deklarace pro dědičnosti nesmí být zdrojový soubor, obor názvů, struktura, modulu, procedura nebo blok.  
  
## <a name="rules"></a>pravidla  
  
-   **Dědičnost tříd.** Pokud používá třídu `Inherits` příkazu, můžete zadat pouze jednu základní třídu.  
  
     Třída nemůže dědit ze třídy do něho vnořený.  
  
-   **Rozhraní dědičnosti.** Pokud používáte rozhraní `Inherits` příkazu, můžete určit jeden nebo více základních rozhraní. Může dědit z dvě rozhraní, i když každá definovat člen se stejným názvem. Pokud tak učiníte, implementující kód používaly kvalifikace názvu určete člen implementuje.  
  
     Rozhraní nemůže dědit z jiného rozhraní s více omezující úroveň přístupu. Například `Public` rozhraní nemůže dědit od třídy `Friend` rozhraní.  
  
     Rozhraní nemůže dědit z rozhraní do něho vnořený.  
  
 Je například dědičnost třídy v rozhraní .NET Framework <xref:System.ArgumentException> třída, která dědí z <xref:System.SystemException> třídy. To poskytuje <xref:System.ArgumentException> předdefinované vlastnosti a postupy vyžadované výjimek systému, například <xref:System.Exception.Message%2A> vlastnost a <xref:System.Exception.ToString%2A> metoda.  
  
 Je například dědičnost rozhraní v rozhraní .NET Framework <xref:System.Collections.ICollection> rozhraní, která dědí z <xref:System.Collections.IEnumerable> rozhraní. To způsobí, že <xref:System.Collections.ICollection> dědění definice výčtu je vyžadováno k procházení kolekce.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Inherits` příkaz Zobrazit jak třída s názvem `thisClass` může dědit všechny členy základní třídy s názvem `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dědičnosti více rozhraní.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 Rozhraní s názvem `thisInterface` teď obsahuje všechny definice v <xref:System.IComparable>, <xref:System.IDisposable>, a <xref:System.IFormattable> rozhraní zděděných členů poskytují v uvedeném pořadí pro konkrétní typ porovnání dvou objektů uvolnění při přidělování prostředků a vyjádření hodnoty objektu jako `String`. Třídu, která implementuje `thisInterface` musíte implementovat každého člena každé základní rozhraní.  
  
## <a name="see-also"></a>Viz také:

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
