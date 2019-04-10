---
title: Serializace a metadata
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c82d32fe5b1e62a19ff5e2920c5943f1303b2d64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207029"
---
# <a name="serialization-and-metadata"></a>Serializace a metadata
Pokud vaše aplikace serializuje a deserializuje objekty, budete muset přidat položky do vašich direktivy modulu runtime (. rd.xml) souboru k zajištění, že je k dispozici v době běhu potřebná metadata. Existují dvě kategorie serializátory a vyžaduje jiný zpracování v souboru direktiv modulu runtime:  
  
-   Serializátory založenými na reflexi třetích stran. Ty vyžadují změny do souboru direktiv modulu runtime a jsou popsané v další části.  
  
-   Na Non reflexi serializátory najdete v knihovně tříd rozhraní .NET Framework. Ty mohou vyžadovat změny do souboru direktiv modulu runtime a jsou popsány v [Microsoft serializátory](#Microsoft) oddílu.  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a>Serializátory třetích stran  
 Třetí část, včetně Newtonsoft.JSON, obvykle serializátory založenými na reflexi. Zadaný binární velkých objektů (BLOB) serializovaných dat, pole v datech jsou přiřazeny k konkrétního typu implementujícího typ vyhledá pole cílového typu podle názvu. Pomocí těchto knihoven způsobí minimálně [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky pro každou <xref:System.Type> objekt, který pokusu o serializaci nebo deserializaci v `List<Type>` kolekce.  
  
 Je nejjednodušší způsob, jak řešit problémy způsobené chybí metadata pro tyto serializátory shromažďovat typy, které se použijí v serializaci v rámci jednoho oboru názvů (jako `App.Models`) a použít `Serialize` směrnice metadata do ní:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Informace o syntaxi použitých v příkladu najdete v tématu [ \<Namespace > Element](../../../docs/framework/net-native/namespace-element-net-native.md).  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a>Microsoft serializátorů  
 I když <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer> třídy není závisí na reflexi, vyžadují kód vygenerování založené na objekt, který má být serializován nebo deserializován. Přetížené konstruktory jednotlivých převodník do sériového tvaru zahrnout <xref:System.Type> parametr, který určuje typ, který má být serializován nebo deserializován. Jak určit, že typ v kódu určuje akci, kterou je třeba provést, jak je popsáno v následujících dvou částech.  
  
### <a name="typeof-used-in-the-constructor"></a>typeof použít v konstruktoru  
 Pokud volání konstruktoru z těchto tříd serializace a uveďte C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) – klíčové slovo ve volání metody **nemusíte dělat nic dalšího**. Například v každé z následujících volání konstruktoru třídy serializace `typeof` – klíčové slovo se používá jako součást výrazu předaný konstruktoru.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilátor automaticky zpracovává tento kód.  
  
### <a name="typeof-used-outside-the-constructor"></a>typeof použít mimo konstruktor  
 Pokud volání konstruktoru z těchto tříd serializace a použít C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) – klíčové slovo mimo výraz zadaný konstruktoru <xref:System.Type> parametr, stejně jako v následujícím kódu [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilátoru Nelze přeložit typ:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 V takovém případě je nutné zadat typ v souboru direktiv modulu runtime přidáním položky jako je tato:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Podobně jako při volání konstruktoru <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> a poskytují celou řadu dalších <xref:System.Type> objekty k serializaci, stejně jako v následujícím kódu [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilátor nemůže vyřešit tyto typy.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Do souboru direktiv modulu runtime, je nutné přidat položky jako je například pro každý typ následující:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Informace o syntaxi použitých v příkladu najdete v tématu [ \<typ > elementu](../../../docs/framework/net-native/type-element-net-native.md).  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
- [\<Typ > – Element](../../../docs/framework/net-native/type-element-net-native.md)
- [\<Namespace > – Element](../../../docs/framework/net-native/namespace-element-net-native.md)
