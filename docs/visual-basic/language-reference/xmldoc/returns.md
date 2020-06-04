---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: edbc374332bdcd67b385ac3d061045664e942460
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84399992"
---
# <a name="returns-visual-basic"></a>\<returns> (Visual Basic)
Určuje návratovou hodnotu vlastnosti nebo funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>Parametry  
 `description`  
 Popis návratové hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Použijte `<returns>` značku v komentáři pro deklaraci metody k popisu návratové hodnoty.  
  
 Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<returns>` značku k vysvětlení, co `DoesRecordExist` funkce vrací.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také

- [Značky pro komentáře XML](index.md)
