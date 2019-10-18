---
title: <list> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 5d4295d485611e75e8b6c8d8f95e079654f0cfa3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524748"
---
# <a name="list-visual-basic"></a>\<list > (Visual Basic)
Definuje seznam nebo tabulku.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
## <a name="parameters"></a>Parametry  
 `type`  
 Typ seznamu U seznamu s odrážkami, "Number" pro číslovaný seznam nebo "Tabulka" pro tabulku se dvěma sloupci musí být "Bullet".  
  
 `term`  
 Používá se pouze v případě, `type` je "Table". Termín, který má definovat, který je definován ve značce Description.  
  
 `description`  
 Pokud je `type` "Bullet" nebo "Number", "`description` je položka v seznamu, pokud `type` je" Table ", `description` je definice `term`.  
  
## <a name="remarks"></a>Poznámky  
 Blok `<listheader>` definuje nadpis tabulky nebo seznamu definic. Při definování tabulky stačí zadat položku pro `term` v záhlaví.  
  
 Každá položka v seznamu je určena pomocí `<item>` bloku. Při vytváření seznamu definic je nutné zadat jak `term`, tak `description`. U tabulky, seznamu s odrážkami nebo číslovaného seznamu ale stačí zadat položku pro `description`.  
  
 Seznam nebo tabulka může mít podle potřeby tolik `<item>` bloků.  
  
 Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá značku `<list>` k definování seznamu s odrážkami v oddílu poznámky.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
