---
title: MID – příkaz (Visual Basic)
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
ms.openlocfilehash: df83fd527612af1a6a4b8131ffa2643ef0d1d7dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784236"
---
# <a name="mid-statement"></a>Mid – příkaz
Nahradí zadaný počet znaků `String` proměnné se znaky z jiného řetězce.  
  
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
 Povinný parametr. Název `String` proměnné, které chcete upravit.  
  
 `Start`  
 Povinný parametr. `Integer` výraz. Znak pozice v `Target` kde začne nahrazování textu. `Start` používá indexu se základem 1.  
  
 `Length`  
 Volitelné. `Integer` výraz. Počet znaků k nahrazení. Pokud tento parametr vynechán, všechny `String` se používá.  
  
 `StringExpression`  
 Povinný parametr. `String` výraz, který nahradí část `Target`.  
  
## <a name="exceptions"></a>Výjimky  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 nebo `Length` < 0.|  
  
## <a name="remarks"></a>Poznámky  
 Počet znaků, které nahradí je vždy menší než počet znaků v `Target`.  
  
 Visual Basic má <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkce a `Mid` příkazu. Tyto prvky obou pracovat na zadaný počet znaků v řetězci, ale `Mid` funkce vrátí znaků při `Mid` příkaz nahradí znaky. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
>  `MidB` Příkaz předchozích verzí jazyka Visual Basic Nahradí podřetězec v bajtů namísto znaků. Používá se především pro převod řetězců v aplikacích dvoubajtové znakové sady (DBCS). Všechny řetězce jazyka Visual Basic jsou v kódování Unicode a `MidB` už není podporovaná.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Mid` příkaz a nahraďte zadaný počet znaků v proměnné typu řetězec znaky z jiného řetězce.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modul:** `Strings`  
  
 **Sestavení:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Řetězce](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Úvod do řetězců v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
