---
title: "Inherits – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae9ba54c3fd1ec3332c9f6260bc19a1293270ad8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="inherits-statement"></a>Inherits – příkaz
Způsobí, že aktuální třídy nebo rozhraní dědění atributy, proměnné, vlastnosti, postupy a události z jiné třídy nebo sadu rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`basetypenames`|Požadováno. Název třídy, ze které je tato třída odvozena.<br /><br /> -nebo-<br /><br /> Názvy rozhraní, ze kterých je odvozena toto rozhraní. K oddělení více názvů používejte čárky.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud se používá, `Inherits` příkaz musí být první neprázdné, bez komentář řádek v definici třídy nebo rozhraní. Okamžitě postupujte `Class` nebo `Interface` příkaz.  
  
 Můžete použít `Inherits` pouze ve třídě nebo rozhraní. To znamená, že deklarace kontext dědičnosti nesmí být zdrojový soubor, obor názvů, struktura, modul, postup nebo bloku.  
  
## <a name="rules"></a>Pravidla  
  
-   **Dědičnost tříd.** Pokud používá třídu `Inherits` prohlášení, můžete zadat pouze jeden základní třídu.  
  
     Třída nemůže Zdědit z ní vnořené třídy.  
  
-   **Rozhraní dědičnosti.** Pokud používá rozhraní `Inherits` prohlášení, můžete určit jeden nebo více základní rozhraní. Může dědit z dvě rozhraní, i v případě, že každý definují člen se stejným názvem. Pokud tak učiníte, implementující kód musíte použít kvalifikace názvu k určení členů, které implementuje.  
  
     Rozhraní nemůže Zdědit z jiné rozhraní s více omezující úroveň přístupu. Například `Public` rozhraní nemůže Zdědit z `Friend` rozhraní.  
  
     Rozhraní nemůže Zdědit z ní vnořené rozhraní.  
  
 Je například dědění tříd v rozhraní .NET Framework <xref:System.ArgumentException> třídy, která dědí z <xref:System.SystemException> třídy. To poskytuje <xref:System.ArgumentException> všechny předdefinované vlastnosti a postupy vyžadované výjimky systému, jako <xref:System.Exception.Message%2A> vlastnost a <xref:System.Exception.ToString%2A> metoda.  
  
 Je například rozhraní dědičnosti v rozhraní .NET Framework <xref:System.Collections.ICollection> rozhraní, které dědí z <xref:System.Collections.IEnumerable> rozhraní. To způsobí, že <xref:System.Collections.ICollection> dědění definici enumerátor požadované procházení kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Inherits` příkaz, který má zobrazit, jak třída s názvem `thisClass` může dědit vlastnosti všechny členy základní třídy s názvem `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dědičnosti více rozhraní.  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 Rozhraní s názvem `thisInterface` nyní zahrnuje všechny definice v <xref:System.IComparable>, <xref:System.IDisposable>, a <xref:System.IFormattable> rozhraní zděděné členy zadejte v uvedeném pořadí pro konkrétní typ porovnání dva objekty, vydání přidělené prostředky a vyjadřující hodnotu objektu jako `String`. Třídu, která implementuje `thisInterface` musí implementovat každého člena každé základní rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
