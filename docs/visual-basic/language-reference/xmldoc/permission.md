---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 6c684a674e8d6e3bf218e0131e5fac2821855456
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966363"
---
# <a name="permission-visual-basic"></a>\<oprávnění > (Visual Basic)
Určuje požadované oprávnění pro tohoto člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a přeloží `member` k názvu canonical prvku ve výstupním souboru XML. Uzavřete `member` do uvozovek ("").  
  
 `description`  
 Popis přístup ke členu.  
  
## <a name="remarks"></a>Poznámky  
 Použití `<permission>` značku k dokumentu přístup člena. Použití <xref:System.Security.PermissionSet> tak, aby určovala přístup ke členu.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<permission>` značka, které popisují, které <xref:System.Security.Permissions.FileIOPermission> vyžaduje `ReadFile` metody.  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Viz také:
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
