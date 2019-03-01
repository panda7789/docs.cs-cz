---
title: <include> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 982e80696e0a8831397197c0c12d748d1d85c349
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978931"
---
# <a name="include-c-programming-guide"></a>\<Zahrnout > (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Název souboru XML, který obsahuje dokumentaci. Název souboru může být kvalifikovány s cestou relativní k souboru se zdrojovým kódem. Uzavřete `filename` v jednoduchých uvozovkách ("").  
  
 `tagpath`  
 Cesta klíčových slov do `filename` , který vede ke značce `name`. Vložte cestu do jednoduchých uvozovek ("").  
  
 `name`  
 Specifikátor názvem ve značce, který předchází komentáře; `name` bude mít `id`.  
  
 `id`  
 ID značky, které předchází komentáře. ID uzavřete do dvojitých uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 \<Zahrnout > značky umožňuje odkazovat na komentáře do jiného souboru, které popisují typy a členy ve zdrojovém kódu. Jedná se o alternativu k uvedení dokumentační komentáře přímo v souboru zdrojového kódu. Vložením dokumentaci v samostatném souboru můžete použít správy zdrojového kódu v dokumentaci samostatně ze zdrojového kódu. Jedna osoba může mít souboru se zdrojovým kódem rezervovat a někdo jiný může mít soubor dokumentace rezervován.  
  
 \<Zahrnout > značky používá syntaxe jazyka XML. XPath dokumentaci pro přizpůsobení vaší \<zahrnout > použít.  
  
## <a name="example"></a>Příklad  
 Toto je vícesouborové příklad. První soubor, který používá \<zahrnout >, která jsou uvedená níže:  
  
 [!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]  
  
 Druhý soubor, xml_include_tag.doc, obsahuje následující komentáře k dokumentaci:  
  
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
 Následující výstup je generována, když kompilujete třídy testu a Test2 s následujícím příkazovým řádkem: `/doc:DocFileName.xml.` V sadě Visual Studio zadejte možnost komentáře XML doc v podokně sestavení Návrháře projektu. Když C# kompilátor narazí \<zahrnout > značky, budou vyhledány dokumentační komentáře ve xml_include_tag.doc namísto aktuálního zdrojového souboru. Kompilátor poté vygeneruje DocFileName.xml a jedná se o soubor, který je využívána dokumentace nástroje, jako například [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) vytvořit finální dokumentaci.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
