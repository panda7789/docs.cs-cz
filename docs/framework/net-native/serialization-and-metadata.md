---
title: Serializace a metadata
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: 1805b6ca06d584237303d1366222419da3e8b9ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128113"
---
# <a name="serialization-and-metadata"></a>Serializace a metadata

Pokud vaše aplikace serializace a deserializace objekty, může být nutné přidat záznamy do souboru direktiv modulu runtime (. Rd. XML), aby bylo zajištěno, že potřebná metadata jsou přítomna v době běhu. Existují dvě kategorie serializátorů a každá z nich vyžaduje jiné zpracování v souboru direktiv modulu runtime:  
  
- Serializátory třetích stran založené na reflexi. Tyto požadavky vyžadují úpravy souboru direktiv modulu runtime a jsou popsány v následující části.  
  
- V knihovně tříd .NET Framework byly nalezeny serializátory založené na reflexi. Ty mohou vyžadovat úpravy souboru direktiv modulu runtime a jsou popsány v části [Microsoft serializátory](#Microsoft) .  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>Serializátory třetích stran

 Serializace jiných částí, včetně Newtonsoft. JSON, jsou obvykle založené na reflexi. Vzhledem k binárnímu velkému objektu (BLOB) serializovaných dat jsou pole v datech přiřazena konkrétnímu typu vyhledáním polí cílového typu podle názvu. Minimálně pomocí těchto knihoven způsobí [MissingMetadataException](missingmetadataexception-class-net-native.md) výjimky pro každý objekt <xref:System.Type>, který se pokoušíte serializovat nebo deserializovat v kolekci `List<Type>`.  
  
 Nejjednodušší způsob, jak řešit problémy způsobené chybějícími metadaty pro tyto serializátory, je shromáždit typy, které budou použity v serializaci v rámci jednoho oboru názvů (například `App.Models`) a použít direktivu `Serialize` metadata:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Informace o syntaxi použité v příkladu naleznete v tématu [\<obor názvů > elementu](namespace-element-net-native.md).  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Serializátory Microsoftu

 I když třídy <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>a <xref:System.Xml.Serialization.XmlSerializer> nespoléhají na reflexi, vyžadují, aby byl kód generován na základě objektu k serializaci nebo deserializaci. Přetížené konstruktory pro každý serializátor zahrnují parametr <xref:System.Type>, který určuje typ, který se má serializovat nebo deserializovat. Způsob určení tohoto typu ve vašem kódu definuje akci, kterou je nutné provést, jak je popsáno v následujících dvou částech.  
  
### <a name="typeof-used-in-the-constructor"></a>typeof použitý v konstruktoru

 Pokud voláte konstruktor těchto tříd serializace a zahrnete C# do volání metody operátor [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) , **není nutné provádět žádnou další práci**. Například v každém z následujících volání konstruktoru třídy serializace je klíčové slovo `typeof` použito jako součást výrazu předaného konstruktoru.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 Kompilátor .NET Native tento kód automaticky zpracuje.  
  
### <a name="typeof-used-outside-the-constructor"></a>typeof se používá mimo konstruktor.

 Pokud voláte konstruktor těchto tříd serializace a použijete C# operátor [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) mimo výraz dodaný do <xref:System.Type> parametru konstruktoru, jako v následujícím kódu, kompilátor .NET Native nemůže přeložit typ:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 V takovém případě je nutné zadat typ do souboru direktiv modulu runtime přidáním položky takto:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Podobně při volání konstruktoru, jako je například <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> a poskytnutí pole dalších <xref:System.Type> objektů k serializaci, jako v následujícím kódu, kompilátor .NET Native nemůže tyto typy vyřešit.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Do souboru direktiv modulu runtime musíte přidat položky jako například následující pro každý typ:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Informace o syntaxi použité v příkladu naleznete v tématu [\<Type > elementu](type-element-net-native.md).  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [\<typ > elementu](type-element-net-native.md)
- [\<> elementu oboru názvů](namespace-element-net-native.md)
