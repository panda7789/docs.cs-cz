---
title: Známé typy kontraktů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: bedf35544454a32ff13856a072779cd70723e989
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857165"
---
# <a name="data-contract-known-types"></a>Známé typy kontraktů dat
<xref:System.Runtime.Serialization.KnownTypeAttribute> Třídy můžete zadat v předstihu, typy, které by měly být zahrnuty k posouzení vlastní během deserializace. Funkční příklad najdete v článku [známé typy](../../../../docs/framework/wcf/samples/known-types.md) příklad.  
  
 Za normálních okolností při předávání parametrů a vrácených hodnot mezi klientem a službou, oba koncové body sdílet všechny kontrakty dat data předávají. Ale to není případ v následujících případech:  
  
- Kontrakt odeslaná data jsou odvozena z smlouvy očekávaná data. Další informace najdete v části o dědičnosti v [ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)). V takovém případě přenášených dat nemá stejná data smlouvy podle očekávání tím přijímající koncový bod.  
  
- Deklarovaný typ informace předávají je rozhraní, na rozdíl od třídy, struktury nebo výčtu. Proto ho nemůže být známé předem jakým typem, že implementuje rozhraní je ve skutečnosti odesílány. a proto přijímající koncový bod nemůže určit předem kontraktu dat pro přenášená data.  
  
- Je deklarovaný typ informace předávají <xref:System.Object>. Protože každý typ dědí z <xref:System.Object>a to nemůže být předem známý typů, které se skutečně přijde, přijímající koncový bod nemůže určit předem kontraktu dat pro přenášená data. Toto je zvláštní případ první položky: Každý kontraktu dat. je odvozena z výchozí prázdné datové kontrakt, který je generován pro <xref:System.Object>.  
  
- Některé typy, mezi které patří [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, mají členy, které jsou v jednom z předchozích tří kategorií. Například <xref:System.Collections.Hashtable> používá <xref:System.Object> k uložení skutečných objektů v zatřiďovací tabulce. Při serializaci těchto typů nelze určit přijímající straně předem kontraktu dat pro tyto členy.  
  
## <a name="the-knowntypeattribute-class"></a>Třída KnownTypeAttribute  
 Po přijetí na koncový bod příjmu dat, pokusí se modul runtime WCF deserializovat data do instance stejného typu language runtime (CLR). Typ, který je vytvořena instance pro deserializaci je vybrán zkontrolováním první příchozí zprávy k určení dat smlouvy tak, aby odpovídal který obsah zprávy. Modul deserializace se pak pokusí se najít typ CLR, který implementuje kontrakt dat kompatibilní s obsah zprávy. Sadu Release candidate typů, které modul deserializace umožňuje během tohoto procesu se označuje jako sada deserializátor "známých typů."  
  
 Jedním ze způsobů, aby modul deserializace vědět o typu je pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute>. Atribut nelze použít pro jednotlivé datové členy pouze pro celé datové typy kontraktu. Atribut je použit *vnějšího typu* , může být třída nebo struktura. Ve své nejzákladnější využití použití atributu určuje typ jako "známý typ". To způsobí, že známý typ jako součást sadu známých typů pokaždé, když se objekt z vnějšího typu nebo libovolný objekt označovány prostřednictvím jejích členů je deserializován. Více než jeden <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut lze použít pro stejného typu.  
  
## <a name="known-types-and-primitives"></a>Známé typy a primitiv  
 Primitivní typy, jakož i určité typy, které jsou považovány za primitivních elementů (například <xref:System.DateTime> a <xref:System.Xml.XmlElement>) jsou vždy "označuje" a už nikdy nemusíte přidají díky tomuto mechanismu. Pole jednoduchých typů je však nutné explicitně přidat. Většina kolekce se považují za ekvivalentní k polím. (Neobecné kolekce se považují za ekvivalentní polí <xref:System.Object>). Příklad pomocí primitiv, primitivní pole a kolekce primitivní, najdete v příkladu 4.  
  
> [!NOTE]
>  Na rozdíl od jiných primitivní typy <xref:System.DateTimeOffset> struktura není známý typ ve výchozím nastavení, takže ho musí ručně přidat do seznamu známých typů.  
  
## <a name="examples"></a>Příklady  
 Následující příklady ukazují <xref:System.Runtime.Serialization.KnownTypeAttribute> třída používá.  
  
#### <a name="example-1"></a>Příklad 1  
 Existují tři třídy s vztah dědičnosti.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Následující `CompanyLogo` třídy lze serializovat, ale nelze deserializovat, pokud `ShapeOfLogo` členů je nastaven na hodnotu `CircleType` nebo `TriangleType` objektu, protože modul deserializace nerozpozná žádné typy s názvy datových kontraktů " Kruh"nebo"Trojúhelník".  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 Správný způsob zápisu `CompanyLogo` typ je znázorněno v následujícím kódu.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Pokaždé, když vnější typ `CompanyLogo2` je deserializován, modul deserializace ví o `CircleType` a `TriangleType` a proto je schopen vyhledat odpovídající typy kontraktů dat "Kruh" a "Trojúhelník".  
  
#### <a name="example-2"></a>Příklad 2  
 V následujícím příkladu i v případě, obě `CustomerTypeA` a `CustomerTypeB` mít `Customer` kontraktu dat, instance `CustomerTypeB` vždy, když se vytvoří `PurchaseOrder` je deserializovat, protože pouze `CustomerTypeB` se ví, modul deserializace.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Příklad 3  
 V následujícím příkladu <xref:System.Collections.Hashtable> ukládá obsah interně jako <xref:System.Object>. Úspěšně deserializovat zatřiďovací tabulku, musíte znát modul deserializace sadu možných typů, které se mohou vyskytnout existuje. V tomto případě jsme předem vědět pouze `Book` a `Magazine` objekty jsou uloženy v `Catalog`, takže ty jsou přidány pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Příklad 4:  
 V následujícím příkladu kontrakt dat ukládá číslo a operace provádět na číslo. `Numbers` Datový člen může být celé číslo, pole celých čísel, nebo <xref:System.Collections.Generic.List%601> obsahující celá čísla.  
  
> [!CAUTION]
>  Bude to fungovat jenom na straně klienta Pokud SVCUTIL. Soubor EXE slouží ke generování WCF proxy. SVCUTIL. Soubor EXE načte metadata ze služby včetně všech známých typů. Bez těchto informací klienta nebude možné deserializovat typy.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Toto je kód aplikace.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Známých typů, dědičnost a rozhraní  
 Pokud je spojené s konkrétní typ použitím známý typ `KnownTypeAttribute` atribut, známý typ je přidružen také všechny odvozené typy tohoto typu. Například viz následující kód.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 `DoubleDrawing` Třída nevyžaduje, aby `KnownTypeAttribute` atribut používat `Square` a `Circle` v `AdditionalShape` pole, protože základní třída (`Drawing`) už má tyto atributy použité.  
  
 Známé typy lze přidružit pouze k tříd a struktur, není rozhraní.  
  
## <a name="known-types-using-open-generic-methods"></a>Známé typy pomocí otevřené obecné metody  
 Může být potřeba přidat jako známý typ obecného typu. Otevřený obecný typ. však nelze předat jako parametr `KnownTypeAttribute` atribut.  
  
 Tento problém můžete vyřešit pomocí alternativní mechanismus: Zapsat metodu, která vrátí seznam typů, který chcete přidat do kolekce známých typů. Název metody je pak zadaný jako argument řetězec k `KnownTypeAttribute` atribut z důvodu určitá omezení.  
  
 Metodu, musí existovat v typu, na který `KnownTypeAttribute` atributu se použije, musí být statická, musí přijmout žádné parametry a musí vrátit objekt, který lze přiřadit k <xref:System.Collections.IEnumerable> z <xref:System.Type>.  
  
 Nelze kombinovat `KnownTypeAttribute` atribut s názvem metody a `KnownTypeAttribute` atributy se skutečné typy na stejného typu. Kromě toho není možné použít více než jeden `KnownTypeAttribute` s názvem metody do stejného typu.  
  
 Podívejte se následující třídy.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 `theDrawing` Obsahuje pole instance generické třídy `ColorDrawing` a obecnou třídu `BlackAndWhiteDrawing`, které dědí z obecné třídy `Drawing`. Za normálních okolností obě musí být přidané do známé typy, ale následující není platnou syntaxi pro atributy.  
  
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
  
 Díky tomu se metoda musí být vytvořený vracet tyto typy. Správný způsob zápisu tohoto typu, zobrazí se v následujícím kódu.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Další způsoby, jak přidat známé typy  
 Kromě toho známé typy, které je možné přidat prostřednictvím konfiguračního souboru. To je užitečné, pokud není ovládací prvek na typ, který vyžaduje známých typů pro správné deserializace, jako je například při použití jiných výrobců zadejte knihovny Windows Communication Foundation (WCF).  
  
 Následující konfigurační soubor ukazuje, jak určit známý typ v konfiguračním souboru.  
  
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
  
 V předchozí konfiguraci souboru typ kontraktu dat s názvem `MyCompany.Library.Shape` je deklarován mít `MyCompany.Library.Circle` jako známý typ.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [Známé typy](../../../../docs/framework/wcf/samples/known-types.md)
- [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md)
