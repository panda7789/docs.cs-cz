---
title: '&lt;zahrnout&gt; (C# Průvodce programováním)'
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: a681a2fcbb874d67b82c8bda73d92dd993928bbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334506"
---
# <a name="ltincludegt-c-programming-guide"></a>&lt;zahrnout&gt; (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Název souboru XML, který obsahuje v dokumentaci. Název souboru může být kvalifikovaný s cestou. Uzavřete `filename` v jednoduchých uvozovkách ("").  
  
 `tagpath`  
 Cesta značky v `filename` který vede ke značce `name`. Vložte cestu do jednoduchých uvozovek ("").  
  
 `name`  
 Specifikátor název ve značce, která předchází komentáře; `name` bude mít `id`.  
  
 `id`  
 ID značky, která předchází komentáře. Uzavřete ID do dvojitých uvozovek nahoře ("").  
  
## <a name="remarks"></a>Poznámky  
 \<Zahrnují > značka umožňuje odkazovat komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu. Jde o alternativu k uvedení dokumentační komentáře ve zdrojovém kódu souboru přímo. V dokumentaci k umístěním v samostatném souboru, můžete použít zdrojového kódu v dokumentaci k samostatně z zdrojového kódu. Jedna osoba může mít přístup k souboru zdrojového kódu rezervovaný, a souborů dokumentace rezervována může mít někdo jiný.  
  
 \<Zahrnují > Značka se používá syntaxe XML XPath. Výraz XPath dokumentaci k tom, jak přizpůsobit vaší \<zahrnují > použít.  
  
## <a name="example"></a>Příklad  
 Toto je příklad více souborů. První soubor, který používá \<zahrnují >, je uvedený níže:  
  
 [!code-csharp[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 Druhý soubor, xml_include_tag.doc, obsahuje následující dokumentační komentáře:  
  
```xml  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a>Výstup programu  
 Tento výstup se vygeneruje, když kompilujete Test a Test2 tříd pomocí následující příkazový řádek: `/doc:DocFileName.xml.` v sadě Visual Studio, zadejte možnost komentáře doc XML v podokně sestavení v Návrháři projektu. Když uvidí kompilátor jazyka C# \<zahrnují > značky, bude hledat pro dokumentační komentáře ve xml_include_tag.doc místo aktuální zdrojový soubor. Kompilátor pak vygeneruje DocFileName.xml, a to je soubor, který využívá dokumentace nástroje, jako [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB) k vytvoření konečné dokumentaci.  
  
```xml  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
