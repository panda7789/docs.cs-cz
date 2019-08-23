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
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963554"
---
# <a name="mid-statement"></a>Mid – příkaz
Nahradí zadaný počet znaků v `String` proměnné znaky z jiného řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Součásti  
 `Target`  
 Povinný parametr. `String` Název proměnné, která se má změnit  
  
 `Start`  
 Povinný parametr. `Integer`vyjádření. Pozice znaku, `Target` kde začíná nahrazování textu. `Start`používá index založený na jednom.  
  
 `Length`  
 Volitelný parametr. `Integer`vyjádření. Počet znaků, které mají být nahrazeny. `String` Je-li tento parametr vynechán, je použita hodnota all.  
  
 `StringExpression`  
 Povinný parametr. `String`výraz, který nahrazuje část `Target`.  
  
## <a name="exceptions"></a>Výjimky  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`< = 0 nebo `Length` < 0.|  
  
## <a name="remarks"></a>Poznámky  
 Počet nahrazených znaků je vždy menší nebo roven počtu znaků v `Target`.  
  
 Visual Basic má <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkci `Mid` a příkaz. Tyto prvky jsou provozovány na zadaném počtu znaků v řetězci, ale `Mid` funkce vrátí znaky, `Mid` zatímco příkaz nahradí znaky. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> `MidB` Příkaz starší verze Visual Basic nahrazuje podřetězec v bajtech namísto znaků. Používá se především pro převod řetězců v aplikacích dvoubajtové znakové sady (DBCS). Všechny Visual Basic řetězce jsou v kódování Unicode a `MidB` již nejsou podporovány.  
  
## <a name="example"></a>Příklad  
 V `Mid` tomto příkladu se používá příkaz k nahrazení zadaného počtu znaků v řetězcové proměnné znaky z jiného řetězce.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Požadavky  
 **Hosting** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modul:** `Strings`  
  
 **Shromážděním** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Řetězce](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Seznámení s řetězci v Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
