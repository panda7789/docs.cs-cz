---
title: '&lt;Hodnota&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: ef14836c438cf6a1de300270d9882c1e53e716ee
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392306"
---
# <a name="ltvaluegt-visual-basic"></a>&lt;Hodnota&gt; (Visual Basic)
Určuje popis vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parametry  
 `property-description`  
 Popis pro vlastnost.  
  
## <a name="remarks"></a>Poznámky  
 Použití `<value>` značku k popisu vlastnosti. Všimněte si, že při přidání vlastnosti pomocí Průvodce kódem ve vývojovém prostředí sady Visual Studio přidá [ \<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) značky pro novou vlastnost. Měli byste pak ručně přidat `<value>` značka, které popisují hodnotu, která představuje vlastnost.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `<value>` značka, které popisují, jaká hodnota `Counter` vlastnost obsahuje.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
