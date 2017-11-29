---
title: "&lt;zahrnout&gt; (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f4df6a23b2fe33b2390aef86891aedc6b04e464d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Doporučené značky pro dokumentační komentáře](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
