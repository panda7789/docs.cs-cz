---
title: Seznam atributů
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: f2400334182d373ea49c130fd17bc4f9943248d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408442"
---
# <a name="attribute-list-visual-basic"></a>Seznam atributů (Visual Basic)
Určuje atributy, které se mají použít u deklarovaného programovacího prvku. Více atributů je odděleno čárkami. Následuje syntaxe pro jeden atribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Součásti  
|||
|---|---|
|`attributemodifier`|Požadováno pro atributy použité na začátku zdrojového souboru. Může být [sestavení](../modifiers/assembly.md) nebo [modul](../modifiers/module-keyword.md).|
|`attributename`| Povinná hodnota. Název atributu|
|`attributearguments`|Nepovinný parametr. Seznam pozičních argumentů pro tento atribut Více argumentů je odděleno čárkami.|
|`attributeinitializer`|Nepovinný parametr. Seznam inicializátorů proměnných nebo vlastností pro tento atribut. Vícenásobné Inicializátory jsou odděleny čárkami.|
  
## <a name="remarks"></a>Poznámky  
 Jeden nebo více atributů můžete použít téměř v jakémkoli programovacím prvku (typy, procedury, vlastnosti a tak dále). Atributy se zobrazí v metadatech sestavení a mohou vám pomohou opatřit poznámky kódem nebo určit, jak použít konkrétní programovací prvek. Můžete použít atributy definované Visual Basic a .NET Framework a můžete definovat vlastní atributy.  

 Další informace o použití atributů najdete v tématu [Přehled atributů](../../programming-guide/concepts/attributes/index.md). Informace o názvech atributů naleznete v tématu [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Pravidla  
  
- **Stáž.** Můžete použít atributy na nejvíce deklarované programovací prvky. Chcete-li použít jeden nebo více atributů, umístěte *blok atributů* na začátek deklarace elementu. Každá položka v seznamu atributů určuje atribut, který chcete použít, a modifikátor a argumenty, které používáte pro toto vyvolání atributu.  
  
- **Lomené závorky** Pokud zadáte seznam atributů, je nutné jej uzavřít do lomených závorek (" `<` " a " `>` ").  
  
- **Část deklarace** Atribut musí být součástí deklarace elementu, nikoli samostatného příkazu. Můžete použít sekvenci pokračování řádku (" `_` ") k roztažení příkazu deklarace na více řádků zdrojového kódu.  
  
- **Modifikátory.** Modifikátor atributu ( `Assembly` nebo `Module` ) je vyžadován u každého atributu použitého pro programovací element na začátku zdrojového souboru. Modifikátory atributu nejsou povoleny u atributů použitých pro prvky, které nejsou na začátku zdrojového souboru.  
  
- **Náhodné.** Všechny Poziční argumenty atributu musí předcházet všem inicializátorům proměnných nebo vlastností.  
  
## <a name="example"></a>Příklad  
 Následující příklad aplikuje <xref:System.Runtime.InteropServices.DllImportAttribute> atribut na kostru definice `Function` procedury.  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute>označuje, že procedura v atributu představuje vstupní bod v nespravované dynamické knihovně (DLL). Atribut poskytuje název knihovny DLL jako poziční argument a další informace jako Inicializátory proměnných.  
  
## <a name="see-also"></a>Viz také

- [Sestavení](../modifiers/assembly.md)
- [Čipu\<keyword>](../modifiers/module-keyword.md)
- [Přehled atributů](../../programming-guide/concepts/attributes/index.md)
- [Postupy: Přerušení a kombinování příkazů v kódu](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
