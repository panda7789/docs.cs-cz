---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 24358a1b004f1cefbfeb3fb8451380ed883841df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411470"
---
# <a name="value-visual-basic"></a>\<value> (Visual Basic)
Určuje popis vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parametry  
 `property-description`  
 Popis vlastnosti  
  
## <a name="remarks"></a>Poznámky  
 Použijte `<value>` značku k popisu vlastnosti. Všimněte si, že při přidání vlastnosti pomocí průvodce kódem ve vývojovém prostředí sady Visual Studio bude přidána [\<summary>](summary.md) značka pro novou vlastnost. Měli byste pak ručně přidat `<value>` značku pro popis hodnoty, kterou vlastnost představuje.  
  
 Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<value>` značku k popisu, jakou hodnotu má `Counter` vlastnost obsahovat.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Značky pro komentáře XML](index.md)
