---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 8f28ecc33eea99150509bb4bade047489b4b826b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352304"
---
# <a name="para-visual-basic"></a>> \<param (Visual Basic)
Určuje, že obsah je formátován jako odstavec.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parametry  
 `content`  
 Text odstavce  
  
## <a name="remarks"></a>Poznámky  
 Značka `<para>` je určena pro použití uvnitř značky, jako je například [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [\<poznámky >](../../../visual-basic/language-reference/xmldoc/remarks.md), nebo [\<vrací >](../../../visual-basic/language-reference/xmldoc/returns.md)a umožňuje přidat do textu strukturu.  
  
 Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá značka `<para>` k rozdělení oddílu poznámky pro metodu `UpdateRecord` na dva odstavce.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
