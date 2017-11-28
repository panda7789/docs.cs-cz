---
title: "Mid – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61d812ef91acc65728b04efc9aa99e3975e71d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="mid-statement"></a>Mid – příkaz
Nahradí zadaný počet znaků `String` proměnné s znaky z jiné řetězce.  
  
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
 Požadováno. Název `String` proměnné, které chcete upravit.  
  
 `Start`  
 Požadováno. `Integer`výraz. Znak pozice v `Target` kde začíná nahrazení textu. `Start`používá indexu se základem jedna.  
  
 `Length`  
 Volitelné. `Integer`výraz. Počet znaků, který má nahradit. Pokud se vynechá, všechny `String` se používá.  
  
 `StringExpression`  
 Požadováno. `String`výraz, který nahradí část `Target`.  
  
## <a name="exceptions"></a>Výjimky  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`< = 0 nebo `Length` < 0.|  
  
## <a name="remarks"></a>Poznámky  
 Počet znaků, nahradí se vždy menší než počet znaků v `Target`.  
  
 Visual Basic má <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkce a `Mid` příkaz. Tyto prvky obě pracovat na zadaný počet znaků v řetězci, ale `Mid` funkce vrací znaky při `Mid` příkaz nahradí znaky. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
>  `MidB` Prohlášení o dřívějších verzích jazyka Visual Basic nahrazuje podřetězce v bajtech, nikoli znaků. Používá se především pro převod řetězců v aplikacích dvoubajtové znakové sady (DBCS). V kódu Unicode, jsou všechny řetězce jazyka Visual Basic a `MidB` již není podporována.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Mid` příkaz, který má zadaný počet znaků v proměnné řetězce nahraďte znaky z jiné řetězce.  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>Požadavky  
 **Namespace:** [Microsoft.VisualBasic –](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modul:**`Strings`  
  
 **Sestavení:**[!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [Řetězce](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Představení řetězců v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
