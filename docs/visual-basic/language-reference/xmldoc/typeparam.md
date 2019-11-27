---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 00cb62827381146c172e0d15a2c64b167c21f025
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352192"
---
# <a name="typeparam-visual-basic"></a>\<typeparam > (Visual Basic)
Definuje název a popis parametru typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Název parametru typu. Název uzavřete do uvozovek ("").  
  
 `description`  
 Popis parametru typu.  
  
## <a name="remarks"></a>Poznámky  
 Použijte značku `<typeparam>` v komentáři pro obecný typ nebo deklaraci obecného člena k popisu jednoho z parametrů typu.  
  
 Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá značka `<typeparam>` k popisu `id` parametru.  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
