---
title: '&lt;oprávnění&gt; - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: bd5849317fbcb5728033fe271f250401a5993ca3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238608"
---
# <a name="ltpermissiongt-c-programming-guide"></a>&lt;oprávnění&gt; (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a přeloží `member` k názvu canonical prvku ve výstupním souboru XML. *člen* musí být uvedena v uvozovkách ("").  
  
 Informace o tom, jak vytvořit cref odkaz na obecný typ, naleznete v tématu [ \<naleznete v tématu >](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Popis přístup ke členu.  
  
## <a name="remarks"></a>Poznámky  
 \<Oprávnění > značky umožňuje dokumentu přístup člena. <xref:System.Security.PermissionSet> Třída umožňuje určit přístup ke členu.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
