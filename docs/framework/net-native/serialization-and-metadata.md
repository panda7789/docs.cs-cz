---
title: Serializace a metadata
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: 7c6fe241fbf92f52abfa0eb66c37bff4d227b4e5
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241916"
---
# <a name="serialization-and-metadata"></a>Serializace a metadata

Pokud vaše aplikace serializuje a reserializuje objekty, bude pravděpodobně nutné přidat položky do souboru direktiv runtime (.rd.xml), abyste zajistili, že potřebná metadata budou přítomna za běhu. Existují dvě kategorie serializátorů a každá vyžaduje jiné zpracování v souboru direktiv runtime:  
  
- Serializátory třetích stran založené na reflexi. Ty vyžadují změny souboru direktiv runtime a jsou popsány v další části.  
  
- Serializátory založené na nereflexi nalezené v knihovně tříd rozhraní .NET Framework. Ty mohou vyžadovat změny souboru direktiv runtime a jsou popsány v části [Microsoft serializers.](#Microsoft)  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>Serializátory jiných výrobců

 Třetí část serializátory, včetně Newtonsoft.JSON, jsou obvykle reflexe-založené. Vzhledem k tomu, binární velký objekt (BLOB) serializovaných dat, pole v datech jsou přiřazeny k konkrétní typ vyhledáním pole cílového typu podle názvu. Použití těchto knihoven přinejmenším způsobí [výjimky MissingMetadataException](missingmetadataexception-class-net-native.md) pro každý <xref:System.Type> objekt, který se pokusíte `List<Type>` serializovat nebo rekonstruovat v kolekci.  
  
 Nejjednodušší způsob, jak řešit problémy způsobené chybějícími metadaty pro tyto serializátory, je shromáždit typy, `App.Models`které budou `Serialize` použity při serializaci v rámci jednoho oboru názvů (například ) a použít na něj direktivu metadat:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Informace o syntaxi použité v příkladu naleznete v [ \<tématu Obor názvů> Element](namespace-element-net-native.md).  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Serializátory společnosti Microsoft

 Přestože <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, <xref:System.Xml.Serialization.XmlSerializer> a třídy nespoléhají na reflexi, vyžadují kód, který má být generován na základě objektu, který má být serializován nebo deserializován. Přetížené konstruktory pro každý serializátor obsahují <xref:System.Type> parametr, který určuje typ, který má být serializován nebo reserializován. Způsob zadání tohoto typu v kódu definuje akci, kterou je třeba provést, jak je popsáno v následujících dvou částech.  
  
### <a name="typeof-used-in-the-constructor"></a>typ použitého v konstruktoru

 Pokud voláte konstruktor těchto tříd serializace a zahrnout [c# typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operátor ve volání metody, **není třeba provést žádnou další práci**. Například v každé z následujících volání konstruktoru `typeof` třídy serializace se klíčové slovo používá jako součást výrazu předaného konstruktoru.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 Nativní kompilátor .NET bude automaticky zpracovávat tento kód.  
  
### <a name="typeof-used-outside-the-constructor"></a>typ použitého mimo konstruktor

 Pokud voláte konstruktor těchto tříd serializace a používáte operátor [C# typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) mimo <xref:System.Type> výraz dodaný parametru konstruktoru, jako v následujícím kódu, kompilátor .NET Native nemůže přeložit typ:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 V takovém případě je nutné zadat typ v souboru direktiv runtime přidáním položky takto:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Podobně pokud voláte konstruktor, <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> například a poskytnout <xref:System.Type> pole další objekty serializovat, jako v následujícím kódu, kompilátor .NET Native nelze vyřešit tyto typy.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Do souboru direktiv direktiv runtime je nutné přidat následující položky, například následující:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Informace o syntaxi použité v [ \<](type-element-net-native.md)příkladu naleznete v tématu Typ> Element .  
  
## <a name="see-also"></a>Viz také

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [\<Typ> element](type-element-net-native.md)
- [\<> element oboru názvů](namespace-element-net-native.md)
