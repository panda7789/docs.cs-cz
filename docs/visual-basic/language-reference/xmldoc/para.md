---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400070"
---
# <a name="para-visual-basic"></a>\<para> (Visual Basic)
Určuje, že obsah je formátován jako odstavec.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parametry  
 `content`  
 Text odstavce  
  
## <a name="remarks"></a>Poznámky  
 `<para>`Značka je určena pro použití uvnitř značky, jako například [\<summary>](summary.md) , [\<remarks>](remarks.md) nebo [\<returns>](returns.md) , a umožňuje přidat do textu strukturu.  
  
 Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<para>` značku k rozdělení oddílu poznámky pro `UpdateRecord` metodu do dvou odstavců.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také

- [Značky pro komentáře XML](index.md)
