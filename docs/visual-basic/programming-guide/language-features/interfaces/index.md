---
title: Rozhraní (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
ms.openlocfilehash: 5f85eca1026d05d8dc3d862559ee48440edf2c4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775931"
---
# <a name="interfaces-visual-basic"></a>Rozhraní (Visual Basic)
*Rozhraní* definovat vlastnosti, metody a události, které můžete implementovat třídy. Rozhraní umožňují definovat funkce jako malé skupiny úzce související vlastnosti, metody a události; To snižuje problémy s kompatibilitou, protože vám umožní vytvářet lepší implementace pro vaše rozhraní bez ohrožující existující kód. Kdykoli můžete přidat nové funkce ve vývoji, implementace a dalších rozhraní.  
  
 Existuje několik jiných důvodů, proč můžete chtít použít rozhraní namísto dědičnosti třídy:  
  
- Rozhraní se lépe hodí pro situace, ve kterých vaše aplikace vyžadují že mnoho pravděpodobně nesouvisejících typů objektů pro poskytnutí některých funkcí.  
  
- Rozhraní jsou flexibilnější, než základní třídy, protože můžete definovat jedna implementace, které můžou implementovat více rozhraní.  
  
- Rozhraní jsou lepší v situacích, ve kterých nemáte implementace dědit ze základní třídy.  
  
- Rozhraní jsou užitečné, pokud nemůžete použít dědičnost tříd. Například struktury nemůže dědit z třídy, ale mohou implementovat rozhraní.  
  
## <a name="declaring-interfaces"></a>Deklarace rozhraní  
 Definice rozhraní jsou uzavřený do složených závorek `Interface` a `End Interface` příkazy. Následující `Interface` příkazu, můžete přidat volitelný `Inherits` příkaz, který obsahuje jeden nebo více zděděných rozhraních. `Inherits` Příkazy musí předcházet před všechny ostatní příkazy v deklaraci s výjimkou komentáře. Zbývající příkazy v definici rozhraní by měl být `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, a `Enum` příkazy. Rozhraní nemůžou obsahovat žádné implementační kód nebo příkazy, které jsou přidružené k provádění kódu, jako například `End Sub` nebo `End Property`.  
  
 V oboru názvů, jsou rozhraní příkazů `Friend` ve výchozím nastavení, ale mohou také být explicitně deklarovány jako `Public` nebo `Friend`. Rozhraní definované v rámci třídy, rozhraní a moduly a struktury jsou `Public` ve výchozím nastavení, ale mohou také být explicitně deklarovány jako `Public`, `Friend`, `Protected`, nebo `Private`.  
  
> [!NOTE]
>  `Shadows` – Klíčové slovo lze použít pro všechny členy rozhraní. `Overloads` – Klíčové slovo lze použít u `Sub`, `Function`, a `Property` příkazy deklarované v definici rozhraní. Kromě toho `Property` příkazů může mít `Default`, `ReadOnly`, nebo `WriteOnly` modifikátory. Žádná z jiných modifikátory –`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, nebo `Overridable`– jsou povoleny. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Například následující kód definuje rozhraní s jednu funkci, jednu vlastnost a jednu událost.  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a>Implementace rozhraní  
 Visual Basic vyhrazené slovo `Implements` slouží dvěma způsoby. `Implements` Prohlášení znamená, že třída nebo struktura implementuje rozhraní. `Implements` – Klíčové slovo znamená, že člen třídy nebo struktury člen implementuje člen konkrétní rozhraní.  
  
### <a name="implements-statement"></a>Implements – Příkaz  
 Pokud jeden nebo více rozhraní implementuje, třídy nebo struktury, musí zahrnovat `Implements` příkaz ihned po `Class` nebo `Structure` příkazu. `Implements` Příkaz vyžaduje čárkou oddělený seznam rozhraní k implementaci třídy. Třída nebo struktura musí implementovat všechny členy rozhraní pomocí `Implements` – klíčové slovo.  
  
### <a name="implements-keyword"></a>Implements – klíčové slovo  
 `Implements` – Klíčové slovo vyžaduje oddělený čárkami seznam členů rozhraní k implementaci. Obecně platí pouze jedno rozhraní člen je zadána, ale můžete zadat více členů. Specifikace člena rozhraní se skládá z názvu rozhraní, který musí být zadán v příkazu implementuje v rámci třídy. období; a název členské funkce, vlastnost nebo událost k implementaci. Jméno člena, který implementuje člen rozhraní, můžete použít libovolný platný identifikátor a se neomezuje `InterfaceName_MethodName` konvence použité v dřívějších verzích jazyka Visual Basic.  
  
 Například následující kód ukazuje, jak deklarujete podprogram s názvem `Sub1` , který implementuje metodu rozhraní:  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 Typy parametrů a návratové typy implementující členu musí odpovídat rozhraní deklaraci vlastnosti nebo člena v rozhraní. Nejběžnější způsob implementace prvek rozhraní se člen, který má stejný název jako rozhraní, jak je znázorněno v předchozím příkladu.  
  
 Chcete-li deklarovat implementaci metody rozhraní, můžete použít všechny atributy, které jsou platné u deklarací metody instance, včetně `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, a `Static`. `Shared` Atribut není platný, protože definuje třídu spíše než metody instance.  
  
 Pomocí `Implements`, můžete je zapsat také jedinou metodu, která implementuje několik metod, které jsou definované v rozhraní, jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 Chcete-li implementovat člen rozhraní, můžete použít privátní člen. Pokud privátní člen implementuje člena rozhraní, tento člen mít k dispozici prostřednictvím rozhraní, i když není k dispozici přímo v objektových proměnných pro třídu.  
  
### <a name="interface-implementation-examples"></a>Příklady implementace rozhraní  
 Třídy, které implementují rozhraní musí implementovat všechny jeho vlastnosti, metody a události.  
  
 Následující příklad definuje dvě rozhraní. Druhé síťové rozhraní, `Interface2`, dědí `Interface1` a definuje další vlastnosti a metody.  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 Následující příklad implementuje `Interface1`, rozhraní definované v předchozím příkladu:  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 V posledním příkladu implementuje `Interface2`, včetně metody zděděné z `Interface1`:  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 Můžete implementovat vlastnost jen pro čtení s vlastností readwrite (to znamená, není nutné deklarovat je jen pro čtení v implementaci třídy).  Implementace rozhraní, že alespoň implementujte členy, které deklaruje rozhraní, ale můžou nabízet další funkce, jako je umožňuje vaše vlastnost jako zapisovatelný.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Návod: Vytvoření a implementace rozhraní](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Poskytuje podrobný postup, který vás provede procesem definování a provádění vlastní rozhraní.|  
|[Odchylky obecných rozhraní](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Tento článek popisuje kovariance a kontravariance v obecných rozhraních a obsahuje seznam variantních obecných rozhraní v rozhraní .NET Framework.|
