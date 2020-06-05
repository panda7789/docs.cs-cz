---
title: Mid – příkaz
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
ms.openlocfilehash: 90408fd8a8cfc9b74c8422d0571d61f8534403f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404447"
---
# <a name="mid-statement"></a>Mid – příkaz
Nahradí zadaný počet znaků v `String` proměnné znaky z jiného řetězce.  
  
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
 Povinná hodnota. Název proměnné, `String` která se má změnit  
  
 `Start`  
 Povinná hodnota. `Integer`vyjádření. Pozice znaku, `Target` kde začíná nahrazování textu. `Start`používá index založený na jednom.  
  
 `Length`  
 Nepovinný parametr. `Integer`vyjádření. Počet znaků, které mají být nahrazeny. Je-li tento parametr vynechán, `String` je použita hodnota all.  
  
 `StringExpression`  
 Povinná hodnota. `String`výraz, který nahrazuje část `Target` .  
  
## <a name="exceptions"></a>Výjimky  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`<= 0 nebo `Length` < 0.|  
  
## <a name="remarks"></a>Poznámky  
 Počet nahrazených znaků je vždy menší nebo roven počtu znaků v `Target` .  
  
 Visual Basic má <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkci a `Mid` příkaz. Tyto prvky jsou provozovány na zadaném počtu znaků v řetězci, ale `Mid` funkce vrátí znaky, zatímco `Mid` příkaz nahradí znaky. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> `MidB`Příkaz starší verze Visual Basic nahrazuje podřetězec v bajtech namísto znaků. Používá se především pro převod řetězců v aplikacích dvoubajtové znakové sady (DBCS). Všechny Visual Basic řetězce jsou v kódování Unicode a `MidB` již nejsou podporovány.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá `Mid` příkaz k nahrazení zadaného počtu znaků v řetězcové proměnné znaky z jiného řetězce.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Požadavky  
 **Obor názvů:** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Modul:**`Strings`  
  
 **Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Řetězce](../../programming-guide/language-features/strings/index.md)
- [Představení řetězců v jazyce Visual Basic](../../programming-guide/language-features/strings/introduction-to-strings.md)
