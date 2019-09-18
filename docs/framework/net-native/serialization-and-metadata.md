---
title: Serializace a metadata
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec8180da9637ec2b2c4e1b432773b4f9f1ac908b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049173"
---
# <a name="serialization-and-metadata"></a>Serializace a metadata

Pokud vaše aplikace serializace a deserializace objekty, může být nutné přidat záznamy do souboru direktiv modulu runtime (. Rd. XML), aby bylo zajištěno, že potřebná metadata jsou přítomna v době běhu. Existují dvě kategorie serializátorů a každá z nich vyžaduje jiné zpracování v souboru direktiv modulu runtime:  
  
- Serializátory třetích stran založené na reflexi. Tyto požadavky vyžadují úpravy souboru direktiv modulu runtime a jsou popsány v následující části.  
  
- V knihovně tříd .NET Framework byly nalezeny serializátory založené na reflexi. Ty mohou vyžadovat úpravy souboru direktiv modulu runtime a jsou popsány v části [Microsoft serializátory](#Microsoft) .  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>Serializátory třetích stran

 Serializace jiných částí, včetně Newtonsoft. JSON, jsou obvykle založené na reflexi. Vzhledem k binárnímu velkému objektu (BLOB) serializovaných dat jsou pole v datech přiřazena konkrétnímu typu vyhledáním polí cílového typu podle názvu. Minimálně pomocí těchto knihoven způsobí [MissingMetadataException](missingmetadataexception-class-net-native.md) výjimky pro každý <xref:System.Type> objekt, který se pokoušíte serializovat nebo deserializovat v `List<Type>` kolekci.  
  
 Nejjednodušší způsob, jak řešit problémy způsobené chybějícími metadaty pro tyto serializátory, je shromáždit typy, které budou použity v serializaci v rámci jednoho oboru názvů `App.Models`(například) a `Serialize` použít pro něj direktivu metadata:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Informace o syntaxi použité v příkladu naleznete v tématu [ \<Namespace > element](namespace-element-net-native.md).  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Serializátory Microsoftu

 I když třídy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.Xml.Serialization.XmlSerializer> , a nespoléhají na reflexi, vyžadují, aby byl kód generován na základě objektu k serializaci nebo deserializaci. <xref:System.Runtime.Serialization.DataContractSerializer> Přetížené konstruktory pro každý serializátor obsahují <xref:System.Type> parametr, který určuje typ, který se má serializovat nebo deserializovat. Způsob určení tohoto typu ve vašem kódu definuje akci, kterou je nutné provést, jak je popsáno v následujících dvou částech.  
  
### <a name="typeof-used-in-the-constructor"></a>typeof použitý v konstruktoru

 Pokud voláte konstruktor těchto tříd serializace a zahrnete C# do volání metody operátor [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) , **není nutné provádět žádnou další práci**. Například v každém z následujících volání konstruktoru `typeof` třídy serializace je klíčové slovo použito jako součást výrazu předaného konstruktoru.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 Kompilátor .NET Native tento kód automaticky zpracuje.  
  
### <a name="typeof-used-outside-the-constructor"></a>typeof se používá mimo konstruktor.

 Pokud voláte konstruktor těchto tříd serializace a použijete C# operátor [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) mimo výraz dodaný <xref:System.Type> parametru konstruktoru, jak je uvedeno v následujícím kódu, kompilátor .NET Native nemůže přeložit typ:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 V takovém případě je nutné zadat typ do souboru direktiv modulu runtime přidáním položky takto:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Podobně při volání konstruktoru <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> , jako je a poskytnutí pole dalších <xref:System.Type> objektů k serializaci, jako v následujícím kódu, kompilátor .NET Native nemůže tyto typy vyřešit.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Do souboru direktiv modulu runtime musíte přidat položky jako například následující pro každý typ:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Informace o syntaxi použité v příkladu naleznete v tématu [ \<Type > element](type-element-net-native.md).  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [\<Typ > element](type-element-net-native.md)
- [\<> – Element oboru názvů](namespace-element-net-native.md)
