---
title: Známé typy kontraktů dat
description: Zjistěte, jak model kontraktu dat používá třídu KnownTypeAttribute k určení typů, které mají být zahrnuty během deserializace v rámci služby WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: 52b0caaaac976893dcf5ef5c228ccc4f53bdbe9e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247478"
---
# <a name="data-contract-known-types"></a>Známé typy kontraktů dat
<xref:System.Runtime.Serialization.KnownTypeAttribute>Třída umožňuje zadat předem typy, které by měly být zahrnuty za účelem posouzení během deserializace. Pracovní příklad naleznete v příkladu [známých typů](../samples/known-types.md) .  
  
 Obvykle při předávání parametrů a vrácení hodnot mezi klientem a službou se oba koncové body sdílí se všemi kontrakty dat dat, která se mají přenést. Nejedná se však o případ v následujících případech:  
  
- Kontrakt odeslaných dat je odvozen od očekávaného kontraktu dat. Další informace najdete v části o dědičnosti v [ekvivalentu kontraktu dat](data-contract-equivalence.md). V takovém případě přenosová data nemají stejný kontrakt dat, jak očekává přijímající koncový bod.  
  
- Deklarovaný typ pro informace, které mají být přeneseny, je rozhraní, na rozdíl od třídy, struktury nebo výčtu. Proto nemůže být znám předem, který typ, který implementuje rozhraní, je skutečně odeslán, a proto koncový bod nemůže určit předem kontrakt dat pro přenesená data.  
  
- Deklarovaný typ pro informace, které mají být přeneseny <xref:System.Object> . Vzhledem k tomu, že každý typ dědí z <xref:System.Object> a nelze jej znát předem, který typ je skutečně odeslán, nemůže koncový bod určit předem kontrakt dat pro přenesená data. Jedná se o zvláštní případ první položky: všechny kontrakty dat jsou odvozeny z výchozího, prázdný kontrakt dat, který je vygenerován pro <xref:System.Object> .  
  
- Některé typy, které zahrnují typy .NET Framework, mají členy, kteří jsou v jedné z předchozích tří kategorií. Například <xref:System.Collections.Hashtable> používá <xref:System.Object> k uložení skutečných objektů v zatřiďovací tabulce. Při serializaci těchto typů nemůže přijímající strana určit předem kontrakt dat pro tyto členy.  
  
## <a name="the-knowntypeattribute-class"></a>Třída KnownTypeAttribute  
 Když data dorazí do přijímajícího koncového bodu, pokusí se modul runtime služby WCF deserializovat data do instance typu modulu CLR (Common Language Runtime). Typ, který je vytvořen pro deserializaci, je vybrán nejprve kontrolou příchozí zprávy a určením kontraktu dat, na který obsah zprávy odpovídá. Modul deserializace se pak pokusí najít typ CLR, který implementuje kontrakt dat kompatibilní s obsahem zprávy. Sada typů kandidátů, které v průběhu tohoto procesu umožňuje modul deserializace, je označována jako sada "známých typů" pro deserializaci.  
  
 Jedním ze způsobů, jak nechat modul deserializace informovat o typu, je pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> . Atribut nelze použít pro jednotlivé datové členy, pouze pro celé typy kontraktů dat. Atribut se aplikuje na *vnější typ* , který může být třída nebo struktura. Ve většině základních použití atributu Určuje použití atributu typ jako "známý typ". To způsobí, že známý typ bude součástí sady známých typů pokaždé, když dojde k deserializaci objektu vnějšího typu nebo jakéhokoliv objektu, na který odkazuje jeho členové. <xref:System.Runtime.Serialization.KnownTypeAttribute>Na stejný typ lze použít více než jeden atribut.  
  
## <a name="known-types-and-primitives"></a>Známé typy a primitivní prvky  
 Primitivní typy a také určité typy považované za primitivní (například <xref:System.DateTime> a <xref:System.Xml.XmlElement> ) jsou vždy "známé" a nikdy nemusí být přidány prostřednictvím tohoto mechanismu. Pole primitivních typů je však nutné přidat explicitně. Většina kolekcí se považuje za ekvivalent polí. (Neobecné kolekce se považují za ekvivalentní k polím z <xref:System.Object> ). Příklad použití primitiv primitivních, primitivních polí a primitivních kolekcí najdete v příkladu 4.  
  
> [!NOTE]
> Na rozdíl od jiných primitivních typů <xref:System.DateTimeOffset> Struktura není ve výchozím nastavení známým typem, proto musí být ručně přidána do seznamu známých typů.  
  
## <a name="examples"></a>Příklady  
 Následující příklady znázorňují <xref:System.Runtime.Serialization.KnownTypeAttribute> třídu, která se používá.  
  
#### <a name="example-1"></a>Příklad 1  
 Existují tři třídy se vztahem dědičnosti.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Následující `CompanyLogo` třídu lze serializovat, ale nelze ji deserializovat, pokud `ShapeOfLogo` je člen nastaven na hodnotu `CircleType` nebo `TriangleType` objekt, protože modul deserializace nerozpoznává žádné typy s názvy kontraktů dat "Circle" nebo "trojúhelníkem".  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 Správný způsob, jak napsat `CompanyLogo` typ, je uveden v následujícím kódu.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Pokaždé, když `CompanyLogo2` je deserializován vnější typ, stroj deserializace ví o `CircleType` a `TriangleType` a, a proto je schopný najít vyhovující typy pro kontrakty dat "Circle" a "trojúhelník".  
  
#### <a name="example-2"></a>Příklad 2  
 V následujícím příkladu, i když obojí `CustomerTypeA` a `CustomerTypeB` má `Customer` kontrakt dat, instance `CustomerTypeB` je vytvořena při každém `PurchaseOrder` deserializaci, protože `CustomerTypeB` je znám pouze modulu deserializace.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Příklad 3  
 V následujícím příkladu <xref:System.Collections.Hashtable> ukládá obsah interně jako <xref:System.Object> . Pro úspěšné deserializaci zatřiďovací tabulky musí modul deserializace znát sadu možných typů, které mohou nastat. V tomto případě víme, že pouze `Book` `Magazine` objekty a jsou uloženy v `Catalog` , takže jsou přidány pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> atributu.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Příklad 4  
 V následujícím příkladu kontrakt dat uchovává číslo a operaci, která se má provést na daném čísle. `Numbers`Datový člen může být celé číslo, pole celých čísel nebo <xref:System.Collections.Generic.List%601> , které obsahuje celá čísla.  
  
> [!CAUTION]
> To bude fungovat jenom na straně klienta, pokud se k vygenerování proxy serveru WCF používá SVCUTIL.EXE. SVCUTIL.EXE načítá metadata ze služby, včetně všech známých typů. Bez těchto informací klient nebude moci deserializovat typy.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Toto je kód aplikace.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Známé typy, dědičnost a rozhraní  
 Pokud je známý typ přidružen k určitému typu pomocí `KnownTypeAttribute` atributu, je známý typ také přidružen ke všem odvozeným typům tohoto typu. Podívejte se například na následující kód.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 Třída nevyžaduje, `DoubleDrawing` `KnownTypeAttribute` aby atribut používal `Square` a `Circle` v `AdditionalShape` poli, protože základní třída ( `Drawing` ) již má tyto atributy použity.  
  
 Známé typy lze přidružit pouze ke třídám a strukturám, nikoli rozhraním.  
  
## <a name="known-types-using-open-generic-methods"></a>Známé typy využívající otevřené obecné metody  
 Může být nutné přidat obecný typ jako známý typ. Otevřený obecný typ však nelze předat jako parametr `KnownTypeAttribute` atributu.  
  
 Tento problém lze vyřešit pomocí alternativního mechanismu: napište metodu, která vrátí seznam typů, které se mají přidat do kolekce známých typů. Název metody je pak zadán jako řetězcový argument pro `KnownTypeAttribute` atribut z důvodu určitých omezení.  
  
 Metoda musí existovat na typu, na který `KnownTypeAttribute` je atribut použit. musí být statická, nesmí přijímat žádné parametry a musí vracet objekt, který lze přiřadit k <xref:System.Collections.IEnumerable> <xref:System.Type> .  
  
 Nemůžete kombinovat `KnownTypeAttribute` atribut s názvem metody a `KnownTypeAttribute` atributy se skutečnými typy na stejném typu. Kromě toho nemůžete použít více než jeden `KnownTypeAttribute` s názvem metody na stejný typ.  
  
 Podívejte se na následující třídu.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 `theDrawing`Pole obsahuje instance obecné třídy `ColorDrawing` a obecné třídy `BlackAndWhiteDrawing` , z nichž obě dědí z obecné třídy `Drawing` . V normálním případě musí být oba přidány ke známým typům, ale následující nejsou platnou syntaxí pro atributy.  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 Proto je nutné vytvořit metodu pro vrácení těchto typů. Správný způsob, jak tento typ napsat, je pak zobrazen v následujícím kódu.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Další způsoby, jak přidat známé typy  
 Kromě toho je možné přidat známé typy prostřednictvím konfiguračního souboru. To je užitečné v případě, že neřídíte typ, který vyžaduje známé typy pro správnou deserializaci, například při použití knihoven typů třetích stran s Windows Communication Foundation (WCF).  
  
 Následující konfigurační soubor ukazuje, jak zadat známý typ v konfiguračním souboru.  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 V předchozím konfiguračním souboru je deklarovaný typ kontraktu dat, `MyCompany.Library.Shape` který má být `MyCompany.Library.Circle` označován jako známý typ.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [Známé typy](../samples/known-types.md)
- [Ekvivalence kontraktů dat](data-contract-equivalence.md)
- [Navrhování kontraktů služby](../designing-service-contracts.md)
