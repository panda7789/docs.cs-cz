---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 240c2131179420834e6dade729ee631c0d7811a4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352175"
---
# <a name="value-visual-basic"></a>\<hodnota > (Visual Basic)
Určuje popis vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parametry  
 `property-description`  
 Popis vlastnosti  
  
## <a name="remarks"></a>Poznámky  
 K popisu vlastnosti použijte značku `<value>`. Všimněte si, že při přidání vlastnosti pomocí průvodce kódem ve vývojovém prostředí sady Visual Studio bude přidána značka [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) pro novou vlastnost. Měli byste pak ručně přidat značku `<value>` k popisu hodnoty, kterou vlastnost představuje.  
  
 Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá značka `<value>` k popisu hodnoty, které vlastnost `Counter` obsahuje.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
