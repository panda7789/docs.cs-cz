---
title: Mid – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: ea22af2eb896542bfc329e087101608e08c45107
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581479"
---
# <a name="mid-statement"></a>Mid – příkaz
Nahradí zadaný počet znaků v proměnné `String` znaky z jiného řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Součásti  
 `Target`  
 Požadováno. Název proměnné `String`, kterou chcete upravit.  
  
 `Start`  
 Požadováno. výraz `Integer` Pozice znaku v `Target`, kde začíná nahrazování textu. `Start` používá index založený na jednom.  
  
 `Length`  
 Volitelné. výraz `Integer` Počet znaků, které mají být nahrazeny. Je-li tento parametr vynechán, je použita veškerá `String`.  
  
 `StringExpression`  
 Požadováno. výraz `String`, který nahrazuje část `Target`.  
  
## <a name="exceptions"></a>Výjimky  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 nebo `Length` < 0.|  
  
## <a name="remarks"></a>Poznámky  
 Počet nahrazených znaků je vždy menší nebo roven počtu znaků v `Target`.  
  
 Visual Basic má funkci <xref:Microsoft.VisualBasic.Strings.Mid%2A> a příkaz `Mid`. Tyto prvky fungují na zadaném počtu znaků v řetězci, ale funkce `Mid` vrátí znaky, zatímco příkaz `Mid` nahrazuje znaky. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> Příkaz `MidB` starších verzí Visual Basic nahrazuje podřetězec v bajtech namísto znaků. Používá se především pro převod řetězců v aplikacích dvoubajtové znakové sady (DBCS). Všechny Visual Basic řetězce jsou v kódování Unicode a `MidB` již nejsou podporovány.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá příkaz `Mid` k nahrazení zadaného počtu znaků v řetězcové proměnné znaky z jiného řetězce.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Požadavky  
 **Obor názvů:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modul:** `Strings`  
  
 **Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Řetězce](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Seznámení s řetězci v Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
