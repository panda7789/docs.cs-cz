---
title: '&lt;oprávnění&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 4fafebf94be350951672f01f2d17bd00d4bab69a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltpermissiongt-visual-basic"></a>&lt;oprávnění&gt; (Visual Basic)
Určuje požadované oprávnění člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor zkontroluje, zda existuje element daného kódu a překládá `member` na element kanonický název ve výstupu XML. Uzavřete `member` v uvozovkách ("").  
  
 `description`  
 Popis přístup ke členu.  
  
## <a name="remarks"></a>Poznámky  
 Použití `<permission>` značky k dokumentu přístup člena. Použití <xref:System.Security.PermissionSet> třídu k určení přístup k členem.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<permission>` značka, které popisují, které <xref:System.Security.Permissions.FileIOPermission> je požadován `ReadFile` metoda.  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
