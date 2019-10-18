---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 904d573514bf35b773d47321b7fd3b6a86e90262
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524697"
---
# <a name="permission-visual-basic"></a>\<permission > (Visual Basic)
Určuje požadované oprávnění pro člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML. Uzavřete `member` do uvozovek ("").  
  
 `description`  
 Popis přístupu ke členovi.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí značky `<permission>` můžete zdokumentovat přístup člena. K určení přístupu ke členu použijte třídu <xref:System.Security.PermissionSet>.  
  
 Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá značka `<permission>` k označení toho, že metoda `ReadFile` vyžaduje <xref:System.Security.Permissions.FileIOPermission>.  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
