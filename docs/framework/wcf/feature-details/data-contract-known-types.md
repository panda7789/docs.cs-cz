---
title: "Známé typy kontraktů dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24d26358c0bf0440b2fbba143629a0e4bda21cec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="data-contract-known-types"></a>Známé typy kontraktů dat
<xref:System.Runtime.Serialization.KnownTypeAttribute> Třída umožňuje zadat v předstihu, typy, které by měl být zahrnutý během deserializace důvodů. Příklad pracovní najdete v tématu [známé typy](../../../../docs/framework/wcf/samples/known-types.md) příklad.  
  
 Za normálních okolností při předávání parametry a návratové hodnoty mezi klientem a služby, oba koncové body sdílejí všechny kontrakty dat dat přenášených. Je to ale není velká písmena v následujících případech:  
  
-   Odeslaná data kontrakt je odvozená od kontrakt očekávaná data. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]v části o dědičnosti v [ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)). V takovém případě velikost přenášených dat nemá stejná data smlouvy podle očekávání tím přijímající koncový bod.  
  
-   Deklarovaný typ informace předávají je rozhraní a třídy, struktury nebo výčet. Proto ho nemůže být známé předem který typ, implementuje rozhraní je ve skutečnosti odeslán, a proto přijímající koncový bod nemůže určit předem kontrakt dat přenášených dat.  
  
-   Deklarovaný typ informace předávají je <xref:System.Object>. Protože každý typ dědí od <xref:System.Object>a ho nemůže být známé předem typů, které se skutečně je odeslán, přijímající koncový bod nemůže určit předem kontrakt data přenášená data. Toto je ve speciálním případě první položka: každých kontrakt dat je odvozena z výchozí, kontrakt prázdné dat, který se vygeneruje pro <xref:System.Object>.  
  
-   Některé typy, které zahrnují [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, mají členy, kteří jsou v jednom z výše uvedených tří skupin. Například <xref:System.Collections.Hashtable> používá <xref:System.Object> k uložení skutečných objektů v zatřiďovací tabulce. Při serializaci těchto typů, nemůže straně příjmu předem určit kontrakt dat pro tyto členy.  
  
## <a name="the-knowntypeattribute-class"></a>KnownTypeAttribute – třída  
 Pokud data dorazí na koncový bod přijímající [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime pokusí deserializuje data do instance stejného typu language runtime (CLR). Typ, který je vytvořena instance pro deserializaci je zvolen zkontrolováním první příchozí zpráva k určení dat smlouvy, na které se shodují obsah zprávy. Modul deserializace se potom pokusí se najít typ CLR, který implementuje kontraktu dat, který je kompatibilní s obsah zprávy. Sadu candidate typů, které modul deserializace umožňuje během tohoto procesu se označuje jako deserializátor sadu "známé typy."  
  
 Jedním ze způsobů umožníte modul deserializace vědět o typu je pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute>. Atribut nelze použít pro jednotlivé datové členy, jenom na celou datové typy kontrakt. Atribut se použije k *vnější typ* , může být třídu nebo strukturu. Ve své nejzákladnější využití použití atribut určuje typ jako "známý typ". To způsobí, že známý typ, který má být součástí sadu známé typy vždy, když objekt vnější typu nebo libovolného objektu uvedené prostřednictvím členů je deserializován. Více než jeden <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut lze použít do stejného typu.  
  
## <a name="known-types-and-primitives"></a>Známé typy a primitivní elementy.  
 Primitivní typy, jakož i některé typy, které jsou považovány za primitiv (například <xref:System.DateTime> a <xref:System.Xml.XmlElement>) jsou vždy "známé" a není nutné je přidat díky tomuto mechanismu. Pole jednoduchých typů je však nutné explicitně přidat. Většina kolekce jsou považovány za ekvivalentní k polím. (Non obecné kolekce jsou považovány za ekvivalentní k pole <xref:System.Object>). Příklad použití primitiv, primitivní pole a primitivní kolekcí, najdete v příkladu 4.  
  
> [!NOTE]
>  Na rozdíl od jiných primitivní typy <xref:System.DateTimeOffset> struktura není známý typ ve výchozím nastavení, a musí být ručně přidat do seznamu známých typů.  
  
## <a name="examples"></a>Příklady  
 Následující příklady zobrazují <xref:System.Runtime.Serialization.KnownTypeAttribute> třída používán.  
  
#### <a name="example-1"></a>Příklad 1  
 Existují tři tříd pomocí vztahu dědičnosti.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Následující `CompanyLogo` třídy lze serializovat, ale nelze deserializovat, pokud `ShapeOfLogo` členů je nastaven na hodnotu `CircleType` nebo `TriangleType` objekt, protože modul deserializace nemůže rozpoznat všechny typy s názvy datových kontraktů " Kruh"nebo"Trojúhelník."  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 Správné způsobu jak psát `CompanyLogo` typ je znázorněno v následujícím kódu.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Vždy, když typ vnější `CompanyLogo2` je deserializován, modul deserializace ví o `CircleType` a `TriangleType` a je proto nemůže najít odpovídající typy pro kontrakty dat "Kruh" a "Trojúhelník".  
  
#### <a name="example-2"></a>Příklad 2  
 V následujícím příkladu i když obě `CustomerTypeA` a `CustomerTypeB` mít `Customer` kontraktů dat, instanci `CustomerTypeB` vždy, když je vytvořena `PurchaseOrder` deserializován, protože pouze `CustomerTypeB` se ví, modul deserializace.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Příklad 3  
 V následujícím příkladu <xref:System.Collections.Hashtable> ukládá její obsah interně jako <xref:System.Object>. Chcete-li úspěšně deserializovat zatřiďovací tabulku, musíte znát modul deserializace sadu možné typy, které se můžou vyskytnout existuje. V takovém případě abychom věděli, předem pouze `Book` a `Magazine` objekty jsou uloženy v `Catalog`, takže těch, které jsou přidány, pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Příklad 4  
 V následujícím příkladu kontrakt dat ukládá číslo a operace provádět na číslo. `Numbers` – Datový člen může být celé číslo, pole celých čísel, nebo <xref:System.Collections.Generic.List%601> obsahující celá čísla.  
  
> [!CAUTION]
>  Bude fungovat pouze na straně klienta Pokud SVCUTIL. EXE slouží ke generování WCF proxy. SVCUTIL. EXE získává metadata ze služby včetně všech známých typů. Bez těchto informací klienta nebude možné k deserializaci typy.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Toto je kód aplikace.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Známé typy, dědičnost a rozhraní  
 Pokud je přidružen konkrétní typ pomocí známých typ `KnownTypeAttribute` atribut známý typ je taky přiřazený všechny odvozené typy daného typu. Například viz následující kód.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 `DoubleDrawing` Třída nevyžaduje, aby `KnownTypeAttribute` atribut používat `Square` a `Circle` v `AdditionalShape` pole, protože základní třídy (`Drawing`) již má tyto atributy použité.  
  
 Známé typy lze přidružit pouze k třídy a struktury, nikoli rozhraní.  
  
## <a name="known-types-using-open-generic-methods"></a>Známé typy pomocí otevřete obecné metody  
 Může být nutné přidat jako známý typ obecného typu. Otevřený obecný typ. však nelze předat jako parametr, který se `KnownTypeAttribute` atribut.  
  
 Tento problém lze vyřešit pomocí alternativní mechanismus: napíše metoda, která vrátí seznam typů, které chcete přidat do kolekce známé typy. Název metody je pak zadaný jako argument řetězec k `KnownTypeAttribute` atribut z důvodu určitá omezení.  
  
 Metodu, musí existovat v typu, na který `KnownTypeAttribute` atributu se použije, musí být statické, musí přijmout žádné parametry a musí vrátit objekt, který lze přiřadit k <xref:System.Collections.IEnumerable> z <xref:System.Type>.  
  
 Nelze kombinovat `KnownTypeAttribute` atribut s názvem metody a `KnownTypeAttribute` atributy s skutečné typy na stejného typu. Kromě toho nelze použít více než jeden `KnownTypeAttribute` s názvem metody do stejného typu.  
  
 Viz následující třídy.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 `theDrawing` Pole obsahuje instance obecné třídy `ColorDrawing` a obecné třídy `BlackAndWhiteDrawing`, které dědí obecné třídy `Drawing`. Za normálních okolností obě musí být přidaný do známé typy, ale toto není platné syntaxe pro atributy.  
  
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
  
 Proto musí být vytvořeny metodu vrátit tyto typy. Správný způsob k zápisu tohoto typu, pak se zobrazí v následujícím kódu.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Další způsoby, jak přidat známé typy  
 Kromě toho mohou být přidány známé typy prostřednictvím konfiguračního souboru. To je užitečné, když není řídit typ, který vyžaduje pro správné deserializace, například při použití jiných výrobců knihovny s typů známé typy [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
 Následujícího konfiguračního souboru ukazuje, jak určit známý typ v konfiguračním souboru.  
  
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
  
 V předchozí konfiguraci souboru typu kontraktu dat s názvem `MyCompany.Library.Shape` je deklarovaná tak, aby měl `MyCompany.Library.Circle` jako známému typu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.KnownTypeAttribute>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Object>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>  
 [Známé typy](../../../../docs/framework/wcf/samples/known-types.md)  
 [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md)
