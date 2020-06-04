---
title: <list>
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
ms.openlocfilehash: 955c1a4c5c5619f908b8d03dbf12360c23574478
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400083"
---
# <a name="list-visual-basic"></a>\<list> (Visual Basic)
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
 Používá se pouze v případě `type` , že je "Table". Termín, který má definovat, který je definován ve značce Description.  
  
 `description`  
 Pokud je `type` "Bullet" nebo "Number", `description` je položka v seznamu, pokud `type` je "Table", `description` je definicí `term` .  
  
## <a name="remarks"></a>Poznámky  
 `<listheader>`Blok definuje nadpis buď tabulky, nebo seznamu definic. Při definování tabulky stačí zadat položku pro `term` v záhlaví.  
  
 Každá položka v seznamu je určena `<item>` blokem. Při vytváření seznamu definic je nutné zadat i `term` `description` . U tabulky, seznamu s odrážkami nebo číslovaného seznamu ale stačí zadat položku pro `description` .  
  
 Seznam nebo tabulka může mít tolik `<item>` bloků, kolik potřebujete.  
  
 Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<list>` značku k definování seznamu s odrážkami v oddílu poznámky.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [Značky pro komentáře XML](index.md)
