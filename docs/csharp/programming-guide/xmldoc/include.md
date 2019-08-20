---
title: <include> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 26241dab70a3b6a0cf80b374868fa759647cd8d9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587997"
---
# <a name="include-c-programming-guide"></a>\<zahrnout > (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
## <a name="parameters"></a>Parametry  
 `filename`  
 Název souboru XML, který obsahuje dokumentaci. Název souboru může být kvalifikován cestou relativní k souboru zdrojového kódu. `filename` Uzavřete do jednoduchých uvozovek (' ').  
  
 `tagpath`  
 Cesta značek v `filename` , která vede k označení `name`. Uzavřete cestu do jednoduchých uvozovek (' ').  
  
 `name`  
 Specifikátor názvu ve značce, který předchází komentářům; `name` bude`id`mít.  
  
 `id`  
 ID značky, která předchází komentář. ID uzavřete do dvojitých uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 Tag \<include > umožňuje odkazování na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu. Toto je alternativa k umístění dokumentačních komentářů přímo do souboru zdrojového kódu. Vložením dokumentace do samostatného souboru můžete použít správu zdrojového kódu v dokumentaci samostatně ze zdrojového kódu. Je možné, že soubor zdrojového kódu je zarezervován a někdo jiný může mít zarezervován soubor dokumentace.  
  
 Tag \<include > používá syntaxi XPath XML. V dokumentaci XPath najdete způsoby přizpůsobení \<použití > zahrnutí.  
  
## <a name="example"></a>Příklad  
 Toto je příklad vícesouborového typu. První soubor, který používá \<> include, je uveden níže:  
  
 [!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]  
  
 Druhý soubor xml_include_tag. doc obsahuje následující dokumentační dokumentaci:  
  
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
 Následující výstup je generován při kompilaci třídy test a Test2 pomocí následujícího příkazového řádku: `/doc:DocFileName.xml.`V aplikaci Visual Studio zadáte možnost komentáře k dokumentu XML v podokně sestavení v Návrháři projektu. Když C# kompilátor uvidí \<značku include >, vyhledá komentáře k dokumentaci v souboru xml_include_tag. doc namísto aktuálního zdrojového souboru. Kompilátor pak vygeneruje DocFileName. XML a jedná se o soubor, který je využíván nástroji dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , k vytvoření konečné dokumentace.  
  
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

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
