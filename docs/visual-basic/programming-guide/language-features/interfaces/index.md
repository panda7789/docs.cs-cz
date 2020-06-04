---
title: Rozhraní
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
ms.openlocfilehash: 90f8e5d4eb7bb6b367ee5ffd4a4323097c6bde9c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405040"
---
# <a name="interfaces-visual-basic"></a>Rozhraní (Visual Basic)
*Rozhraní* definují vlastnosti, metody a události, které třídy mohou implementovat. Rozhraní umožňují definovat funkce jako malé skupiny úzce souvisejících vlastností, metod a událostí. Tím se sníží problémy s kompatibilitou, protože můžete vyvíjet rozšířená implementace pro vaše rozhraní bez nutnosti přecházet z existujícího kódu. Nové funkce můžete kdykoli přidat pomocí vývoje dalších rozhraní a implementací.  
  
 Existuje několik dalších důvodů, proč možná budete chtít použít rozhraní namísto dědičnosti tříd:  
  
- Rozhraní jsou lépe vhodná pro situace, kdy vaše aplikace vyžadují mnoho možných nesouvisejících typů objektů, které poskytují určité funkce.  
  
- Rozhraní jsou pružnější než základní třídy, protože lze definovat jednu implementaci, která může implementovat více rozhraní.  
  
- Rozhraní jsou lépe v situacích, kdy není nutné dědit implementaci ze základní třídy.  
  
- Rozhraní jsou užitečná, když nemůžete použít dědičnost tříd. Struktury například nemohou dědit z tříd, ale mohou implementovat rozhraní.  
  
## <a name="declaring-interfaces"></a>Deklarace rozhraní  
 Definice rozhraní jsou uzavřeny v `Interface` `End Interface` příkazech a. Po `Interface` příkazu můžete přidat volitelný `Inherits` příkaz, který zobrazí seznam jednoho nebo více zděděných rozhraní. `Inherits`Příkazy musí předcházet před všemi ostatními příkazy v deklaraci s výjimkou komentářů. Zbývající příkazy v definici rozhraní by měly být `Event` příkazy,,,,, `Sub` `Function` `Property` `Interface` `Class` , `Structure` a `Enum` . Rozhraní nemůžou obsahovat žádný implementační kód ani příkazy spojené s implementačním kódem, jako je například `End Sub` nebo `End Property` .  
  
 V oboru názvů jsou příkazy rozhraní `Friend` ve výchozím nastavení, ale lze je také explicitně deklarovat jako `Public` nebo `Friend` . Rozhraní definovaná v rámci tříd, modulů, rozhraní a struktur jsou `Public` ve výchozím nastavení, ale mohou být také explicitně deklarována `Public` jako `Friend` , `Protected` , nebo `Private` .  
  
> [!NOTE]
> `Shadows`Klíčové slovo lze použít pro všechny členy rozhraní. `Overloads`Klíčové slovo lze použít pro `Sub` příkazy, `Function` a `Property` deklarované v definici rozhraní. Kromě toho `Property` příkazy mohou mít `Default` `ReadOnly` `WriteOnly` modifikátory, nebo. Žádný z ostatních modifikátorů – `Public` , `Private` , `Friend` , `Protected` , `Shared` , `Overrides` , `MustOverride` nebo `Overridable` – jsou povoleny. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Například následující kód definuje rozhraní s jednou funkcí, jednu vlastnost a jednu událost.  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a>Implementace rozhraní  
 Vyhrazené slovo Visual Basic `Implements` se používá dvěma způsoby. `Implements`Příkaz znamená, že třída nebo struktura implementuje rozhraní. `Implements`Klíčové slovo označuje, že člen třídy nebo člen struktury implementuje konkrétního člena rozhraní.  
  
### <a name="implements-statement"></a>Implements – Příkaz  
 Pokud třída nebo struktura implementuje jedno nebo více rozhraní, musí obsahovat `Implements` příkaz hned za `Class` `Structure` příkazem or. `Implements`Příkaz vyžaduje čárkami oddělený seznam rozhraní, která má být implementována třídou. Třída nebo struktura musí implementovat všechny členy rozhraní pomocí `Implements` klíčového slova.  
  
### <a name="implements-keyword"></a>Klíčové slovo Implements  
 `Implements`Klíčové slovo vyžaduje, aby byly implementovány čárkami oddělený seznam členů rozhraní. Obecně je určen pouze jeden člen rozhraní, ale lze zadat více členů. Specifikace člena rozhraní se skládá z názvu rozhraní, který musí být zadán v příkazu Implements v rámci třídy; období; a název členské funkce, vlastnost nebo událost, která má být implementována. Název členu, který implementuje člena rozhraní, může použít jakýkoliv platný identifikátor a není omezen na `InterfaceName_MethodName` konvenci použitou v dřívějších verzích Visual Basic.  
  
 Například následující kód ukazuje, jak deklarovat podprogram s názvem `Sub1` , který implementuje metodu rozhraní:  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 Typy parametrů a návratové typy implementující člena se musí shodovat s vlastností rozhraní nebo deklarací členů v rozhraní. Nejběžnější způsob, jak implementovat element rozhraní, je člen, který má stejný název jako rozhraní, jak je znázorněno v předchozím příkladu.  
  
 Chcete-li deklarovat implementaci metody rozhraní, můžete použít všechny atributy, které jsou platné pro deklarace metod instance, včetně `Overloads` , `Overrides` , `Overridable` , `Public` , `Private` , `Protected` , `Friend` , `Protected Friend` ,, a `MustOverride` `Default` `Static` . `Shared`Atribut není platný, protože definuje třídu namísto metody instance.  
  
 Pomocí `Implements` , můžete také napsat jedinou metodu, která implementuje více metod definovaných v rozhraní, jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 Můžete použít privátního člena k implementaci člena rozhraní. Když soukromý člen implementuje člen rozhraní, bude tento člen dostupný prostřednictvím rozhraní, i když není k dispozici přímo na objektových proměnných pro třídu.  
  
### <a name="interface-implementation-examples"></a>Příklady implementace rozhraní  
 Třídy, které implementují rozhraní, musí implementovat všechny jeho vlastnosti, metody a události.  
  
 Následující příklad definuje dvě rozhraní. Druhé rozhraní `Interface2` dědí `Interface1` a definuje další vlastnost a metodu.  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 Následující příklad implementuje `Interface1` rozhraní definované v předchozím příkladu:  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 Konečný příklad implementuje `Interface2` , včetně metody zděděné z `Interface1` :  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 Můžete implementovat vlastnost jen pro čtení s vlastností ReadOnly (to znamená, že ji nemusíte deklarovat jen pro čtení v implementaci třídy).  Implementace rozhraní příslibů k implementaci alespoň členů, které rozhraní deklaruje, ale můžete nabízet více funkcí, jako je například umožnění zapisovatelné vlastnosti.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Návod: Vytvoření a implementace rozhraní](walkthrough-creating-and-implementing-interfaces.md)|Poskytuje podrobný postup, který vás provede procesem definování a implementace vlastního rozhraní.|  
|[Odchylky obecných rozhraní](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Popisuje kovarianci a kontravariance v obecných rozhraních a poskytuje seznam variantních obecných rozhraní v .NET Framework.|
