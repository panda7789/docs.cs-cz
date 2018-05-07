---
title: Serializace a metadata
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e4db59da7a17e47b8e3df939ec64f5124e04454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="serialization-and-metadata"></a>Serializace a metadata
Pokud vaše aplikace serializuje a deserializuje objekty, budete muset přidat položky do vaší direktivy modulu runtime (. rd.xml) souboru a zajistit tak potřeby metadata nachází v době běhu. Existují dvě kategorie serializátorů a každý vyžaduje jiný zpracování v souboru direktivy modulu runtime:  
  
-   Na základě reflexe serializátorů třetích stran. Tyto vyžadovat změny do souboru direktivy modulu runtime a jsou popsané v další části.  
  
-   Non-odrazových serializátorů najít v knihovně tříd rozhraní .NET Framework. To může vyžadovat změny do souboru direktivy modulu runtime a jsou popsané v [Microsoft serializátorů](#Microsoft) části.  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a>Serializátorů třetích stran  
 Serializátorů třetí součást, včetně Newtonsoft.JSON, jsou obvykle založené na reflexi. Zadaný binární rozsáhlý objekt (binární rozsáhlý OBJEKT) serializovaných dat, pole v datech jsou přiřazeny na konkrétní typ vyhledáním pole cílového typu podle názvu. Pomocí těchto knihoven způsobí minimálně [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky pro každou <xref:System.Type> objekt, který zkuste k serializaci nebo deserializaci v `List<Type>` kolekce.  
  
 Nejjednodušší způsob, jak řešit problémy způsobené chybí metadata pro tyto serializátorů je ke shromažďování typy, které se použijí v serializaci v rámci jednoho oboru názvů (například `App.Models`) a použít `Serialize` – direktiva metadata k němu:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Informace o syntaxi použitých v tomto příkladu najdete v tématu [ \<Namespace > Element](../../../docs/framework/net-native/namespace-element-net-native.md).  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a>Microsoft serializátorů  
 I když <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer> třídy nespoléhejte na reflexi, vyžadují kód, který má být vygenerován založené na objekt, který má být serializován nebo deserializován. Zahrnout přetížené konstruktory pro každý serializátor <xref:System.Type> parametr, který určuje typ, který má být serializován nebo deserializován. Akci, kterou je nutné provést, jak určit typu ve vašem kódu definuje, jak je popsáno v následujících dvou částech.  
  
### <a name="typeof-used-in-the-constructor"></a>typeof použít v konstruktoru  
 Pokud volání konstruktoru tyto třídy serializace a zahrnují jazyka C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) – klíčové slovo v volání metody **nemusíte dělat nic dalšího**. V každé z následujících volání konstruktoru třídy serializace, například `typeof` – klíčové slovo slouží jako součást výrazu předaný konstruktoru.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilátoru automaticky zpracuje tento kód.  
  
### <a name="typeof-used-outside-the-constructor"></a>typeof použít mimo konstruktoru  
 Pokud volání konstruktoru tyto třídy serializace a použití jazyka C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) – klíčové slovo mimo výraz zadaný konstruktoru <xref:System.Type> parametru, jako v následujícím kódu [!INCLUDE[net_native](../../../includes/net-native-md.md)] nelze kompilátoru vyřešení typu:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 V takovém případě musíte zadat typ v souboru direktivy modulu runtime přidáním položky takto:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Podobně, jako při volání konstruktoru <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> a poskytují řadu dalších <xref:System.Type> objekty, které chcete serializovat jako v následujícím kódu [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilátoru nelze vyřešit tyto typy.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Je nutné přidat položky například následující pro každý typ souboru direktivy modulu runtime:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Informace o syntaxi použitých v tomto příkladu najdete v tématu [ \<typ > elementu](../../../docs/framework/net-native/type-element-net-native.md).  
  
## <a name="see-also"></a>Viz také  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [\<Typ > elementu](../../../docs/framework/net-native/type-element-net-native.md)  
 [\<Namespace > elementu](../../../docs/framework/net-native/namespace-element-net-native.md)
