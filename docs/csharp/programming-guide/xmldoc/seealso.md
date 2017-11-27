---
title: "&lt;Viz také&gt; (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 088445680375e1c1805f9fb4356fe98c730178e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltseealsogt-c-programming-guide"></a>&lt;Viz také&gt; (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.`member` musí být v rámci dvojitých uvozovek nahoře ("").  
  
 Informace o tom, jak vytvořit cref odkaz na obecného typu najdete v tématu [ \<najdete v části >](../../../csharp/programming-guide/xmldoc/see.md).  
  
## <a name="remarks"></a>Poznámky  
 \<Seealso > značka umožňuje zadat text, který chcete zobrazit v části Viz také. Použití [ \<najdete v části >](../../../csharp/programming-guide/xmldoc/see.md) zadat odkaz z v textu.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tématu [ \<souhrnné >](../../../csharp/programming-guide/xmldoc/summary.md) příklad použití \<seealso >.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Doporučené značky pro dokumentační komentáře](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
