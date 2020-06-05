---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: b3acec04060367a0b9e54b19c0106644d028357b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400031"
---
# <a name="permission-visual-basic"></a>\<permission> (Visual Basic)
Určuje požadované oprávnění pro člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá se na `member` název kanonického prvku ve výstupním souboru XML. Uzavřete `member` do uvozovek ("").  
  
 `description`  
 Popis přístupu ke členovi.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `<permission>` značky můžete zdokumentovat přístup člena. Použijte <xref:System.Security.PermissionSet> třídu k určení přístupu ke členu.  
  
 Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<permission>` značku k označení toho, že <xref:System.Security.Permissions.FileIOPermission> Metoda je vyžadována `ReadFile` metodou.  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Viz také

- [Značky pro komentáře XML](index.md)
