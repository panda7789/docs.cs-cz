---
title: '&lt;Hodnota&gt; (C# Průvodce programováním)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ea900c21c2c0477c626be5eff2403312d9e8609
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltvaluegt-c-programming-guide"></a>&lt;Hodnota&gt; (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parametry  
 `property-description`  
 Popis pro vlastnost.  
  
## <a name="remarks"></a>Poznámky  
 \<Hodnotu > značka umožňuje popisují hodnotu, která představuje vlastnost. Všimněte si, že pokud přidáte vlastnost prostřednictvím Průvodce kódu ve vývojovém prostředí sady Visual Studio .NET, přidá [ \<souhrnné >](../../../csharp/programming-guide/xmldoc/summary.md) značky pro novou vlastnost. Měli byste pak přidat ručně \<hodnotu > značka, které popisují hodnotu, která představuje vlastnost.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Doporučené značky pro dokumentační komentáře](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
