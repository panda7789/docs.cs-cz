---
title: Rozhraní (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
ms.openlocfilehash: 8380778398495fe9948e6a0eb19b535656a575f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654419"
---
# <a name="interfaces-visual-basic"></a>Rozhraní (Visual Basic)
*Rozhraní* definovat vlastnosti, metod a události, které můžete implementovat třídy. Rozhraní umožňují definovat funkce jako malé skupiny úzce související vlastnosti, metod a událostí; To snižuje problémy s kompatibilitou, protože rozšířené implementace pro vaše rozhraní můžete vyvíjet bez ohrožující existujícího kódu. Kdykoli můžete přidat nové funkce ve vývoji implementace a další rozhraní.  
  
 Tady je několik dalších důvodů, proč můžete chtít použít rozhraní místo dědičnosti tříd:  
  
-   Rozhraní jsou však vhodnější na situace, ve kterých vaše aplikace vyžadují, že mnoho pravděpodobně nesouvisející typy objektů chcete poskytnout určité funkce.  
  
-   Rozhraní jsou flexibilnější než základní třídy, protože můžete definovat jeden implementace, která můžete implementovat více rozhraní.  
  
-   Rozhraní jsou lepší v situacích, ve kterých nemáte základní třídy dědí implementace.  
  
-   Rozhraní jsou užitečné, pokud nelze použít dědičnosti tříd. Například struktury nelze dědí z třídy, ale jejich můžete implementovat rozhraní.  
  
## <a name="declaring-interfaces"></a>Deklarování rozhraní  
 Definice rozhraní jsou uzavřené v rámci `Interface` a `End Interface` příkazy. Následující `Interface` prohlášení, můžete přidat volitelný `Inherits` příkaz, který obsahuje seznam jednoho nebo více zděděné rozhraní. `Inherits` Příkazy musí předcházet jiné příkazy v deklaraci s výjimkou komentáře. Zbývající příkazy v definici rozhraní by měl být `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, a `Enum` příkazy. Rozhraní nemůže obsahovat žádné implementaci kódu nebo příkazy související s implementací kód, jako například `End Sub` nebo `End Property`.  
  
 V oboru názvů, jsou příkazy rozhraní `Friend` ve výchozím nastavení, ale jejich lze také explicitně deklarovat jako `Public` nebo `Friend`. Rozhraní definované v rámci třídy, moduly, rozhraní, a jsou struktury `Public` ve výchozím nastavení, ale jejich lze také explicitně deklarovat jako `Public`, `Friend`, `Protected`, nebo `Private`.  
  
> [!NOTE]
>  `Shadows` – Klíčové slovo lze použít na všechny členy rozhraní. `Overloads` – Klíčové slovo lze použít pro `Sub`, `Function`, a `Property` příkazy deklarované v definici rozhraní. Kromě toho `Property` může mít příkazy `Default`, `ReadOnly`, nebo `WriteOnly` modifikátory. Žádná z jiných modifikátory –`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, nebo `Overridable`– jsou povoleny. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Například následující kód definuje rozhraní s jednu funkci, jednu vlastnost a jednu událost.  
  
 [!code-vb[VbVbalrOOP#17](../../../../visual-basic/misc/codesnippet/VisualBasic/index_1.vb)]  
  
## <a name="implementing-interfaces"></a>Implementace rozhraní  
 Visual Basic vyhrazené slovo `Implements` slouží dvěma způsoby. `Implements` Příkaz označuje, že třídu nebo strukturu implementuje rozhraní. `Implements` – Klíčové slovo označuje, že struktura člena nebo člena třídy implementuje členem konkrétní rozhraní.  
  
### <a name="implements-statement"></a>Implements – Příkaz  
 Pokud třídu nebo strukturu implementuje jedno nebo více rozhraní, musí obsahovat `Implements` příkaz ihned po `Class` nebo `Structure` příkaz. `Implements` Příkaz vyžaduje čárkami oddělený seznam rozhraní k implementaci třídou. Třídu nebo strukturu musí implementovat všichni členové rozhraní pomocí `Implements` – klíčové slovo.  
  
### <a name="implements-keyword"></a>Implements – klíčové slovo  
 `Implements` – Klíčové slovo vyžaduje čárkami oddělený seznam členů rozhraní k implementaci. Obecně platí pouze členem jedné rozhraní je zadána, ale můžete zadat více členů. Specifikace člena rozhraní se skládá z názvu rozhraní, které musí být zadané v příkazu implementuje v rámci třídy; období; a název členské funkce, vlastnost nebo událost, která má být implementována. Název člena, který implementuje rozhraní člen lze použít jakýkoliv povolený identifikátor a není omezen na `InterfaceName_MethodName` konvence používal v dřívějších verzích jazyka Visual Basic.  
  
 Například následující kód ukazuje, jak deklarovat podprogramu s názvem `Sub1` , která implementuje metodu rozhraní:  
  
 [!code-vb[VbVbalrOOP#69](../../../../visual-basic/misc/codesnippet/VisualBasic/index_2.vb)]  
  
 Typy parametrů a návratové typy implementuje člena musí odpovídat deklarace vlastnosti nebo člen rozhraní v rozhraní. Nejběžnější způsob implementace element rozhraní je s člena, který má stejný název jako rozhraní, jak je znázorněno v předchozím příkladu.  
  
 Deklarovat implementace metody rozhraní, můžete použít všechny atributy, které jsou právní na deklarace metody instance, včetně `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, a `Static`. `Shared` Atribut není právní, protože definuje třídu, nikoli metodu instance.  
  
 Pomocí `Implements`, je také možné zapsat jednu metodu, která implementuje několik metod, které jsou definované v rozhraní, jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrOOP#70](../../../../visual-basic/misc/codesnippet/VisualBasic/index_3.vb)]  
  
 Privátního člena můžete použít k implementaci člena rozhraní. Při privátního člena implementuje členem rozhraní, tento člen k dispozici prostřednictvím rozhraní, i když není k dispozici přímo na objektové proměnné pro třídu.  
  
### <a name="interface-implementation-examples"></a>Příklady implementace rozhraní  
 Třídy, které implementují rozhraní musí implementovat všechny jeho vlastnosti, metod a události.  
  
 V následujícím příkladu definuje dvě rozhraní. Rozhraní druhý `Interface2`, dědí `Interface1` a definuje další vlastnosti a metody.  
  
 [!code-vb[VbVbalrOOP#39](../../../../visual-basic/misc/codesnippet/VisualBasic/index_4.vb)]  
  
 Další příklad implementuje `Interface1`, rozhraní definované v předchozím příkladu:  
  
 [!code-vb[VbVbalrOOP#40](../../../../visual-basic/misc/codesnippet/VisualBasic/index_5.vb)]  
  
 Poslední příklad implementuje `Interface2`, včetně metodu zděděno z `Interface1`:  
  
 [!code-vb[VbVbalrOOP#41](../../../../visual-basic/misc/codesnippet/VisualBasic/index_6.vb)]  
  
 Můžete implementovat vlastnost readonly s vlastností readwrite (to znamená, není nutné deklarovat je jen pro čtení v implementující třídu).  Implementace rozhraní k implementaci alespoň členy, kteří rozhraní deklaruje nabízí, ale můžete nabídnout další funkce, například povolení vaší vlastnost, která má být zapisovatelný.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Návod: Vytvoření a implementace rozhraní](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Poskytuje podrobný postup, který vás provede procesem definování a implementace vlastní rozhraní.|  
|[Odchylky obecných rozhraní](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Popisuje kovariance a kontravariance v obecných rozhraní a poskytuje seznam variantních obecných rozhraní v rozhraní .NET Framework.|
