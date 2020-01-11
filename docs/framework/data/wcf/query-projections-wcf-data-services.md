---
title: Projekce dotazů (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: 764ea6a77ba267e691d48bc72d17c02f6b3c18ca
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900973"
---
# <a name="query-projections-wcf-data-services"></a>Projekce dotazů (WCF Data Services)

Projekce poskytuje mechanismus v protokolu OData (Open Data Protocol) k omezení množství dat v kanálu vrácených dotazem tím, že zadáte, že v odpovědi se vrátí jenom některé vlastnosti entity. Další informace najdete v části 4,8. V konvencích identifikátoru URI vyberte možnost dotaz na systém ($select) [(OData verze 2,0)](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).

Toto téma popisuje, jak definovat projekci dotazu, jaké jsou požadavky pro entity a typy bez entit, které provádějí aktualizace s plánovanými výsledky, vytváření projektových typů a uvádí některé informace o projekci.

## <a name="defining-a-query-projection"></a>Definování projekce dotazu

Klauzuli projekce můžete k dotazu přidat buď pomocí možnosti dotazu `$select` v identifikátoru URI, nebo pomocí klauzule [Select](../../../csharp/language-reference/keywords/select-clause.md) ([Select](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) v dotazu LINQ. Vrácená data entity lze v klientovi promítnout buď na typy entit, nebo na typy bez entit. Příklady v tomto tématu ukazují, jak použít klauzuli `select` v dotazu LINQ.

> [!IMPORTANT]
> Při ukládání aktualizací, které byly provedeny s plánovanými typy, může dojít ke ztrátě dat v datové službě. Další informace najdete v tématu věnovaném [projekčním hlediskům](#considerations).

## <a name="requirements-for-entity-and-non-entity-types"></a>Požadavky na typy entit a jiných entit

Typy entit musí mít jednu nebo více vlastností identity, které tvoří klíč entity. Typy entit jsou definovány v klientech jedním z následujících způsobů:

- Použitím <xref:System.Data.Services.Common.DataServiceKeyAttribute> nebo <xref:System.Data.Services.Common.DataServiceEntityAttribute> na typ.

- Když typ obsahuje vlastnost s názvem `ID`.

- Když typ obsahuje vlastnost s názvem *type*`ID`, kde *Type* je název typu.

Ve výchozím nastavení se při dotazování výsledků dotazu na typ definovaný v klientovi musí v typu klienta vyskytovat vlastnosti požadované v projekci. Pokud však zadáte hodnotu `true` pro vlastnost <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> <xref:System.Data.Services.Client.DataServiceContext>, není nutné, aby v typu klienta docházelo k vlastnostem zadaným v projekci.

### <a name="making-updates-to-projected-results"></a>Provádění aktualizací s plánovanými výsledky

Při dotazování výsledků dotazu na typy entit v klientovi mohou <xref:System.Data.Services.Client.DataServiceContext> sledovat tyto objekty s aktualizacemi, které se mají odeslat zpět do datové služby, když je volána metoda <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>. Aktualizace provedené v datech, které se procházejí na typy neentitované v klientovi, se ale nedají poslat zpátky do datové služby. Důvodem je to, že bez klíče k identifikaci instance entity nemůže datová služba aktualizovat správnou entitu ve zdroji dat. Typy bez entit nejsou k <xref:System.Data.Services.Client.DataServiceContext>připojeny.

V případě, že jedna nebo více vlastností typu entity definovaného v datové službě se neobjeví v typu klienta, do kterého je entita provedená, vkládání nových entit nebudou obsahovat tyto chybějící vlastnosti. V takovém případě nebudou aktualizace provedené u stávajících entit obsahovat **také** tyto chybějící vlastnosti. Pokud pro takovou vlastnost existuje hodnota, aktualizace ji obnoví na výchozí hodnotu vlastnosti, jak je definováno ve zdroji dat.

### <a name="creating-projected-types"></a>Vytváření projektových typů

V následujícím příkladu je použit anonymní dotaz LINQ, který je projektem vlastností souvisejících s adresou `Customers` typu do nového typu `CustomerAddress`, který je definován v klientovi a má atribut jako typ entity:

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

V tomto příkladu je použit vzor inicializátoru objektu k vytvoření nové instance `CustomerAddress` typu namísto volání konstruktoru. Konstruktory nejsou podporovány při projekci do typů entit, ale lze je použít při projekci na jiné než entity a anonymní typy. Vzhledem k tomu, že `CustomerAddress` je typ entity, lze provést změny a odeslat je zpět do datové služby.

Data z `Customer`ho typu se také prochází do instance typu entity `CustomerAddress` namísto anonymního typu. Projekce na anonymní typy je podporována, ale data jsou jen pro čtení, protože anonymní typy jsou považovány za typy bez entit.

Nastavení <xref:System.Data.Services.Client.MergeOption> <xref:System.Data.Services.Client.DataServiceContext> se používá pro rozlišení identity během projekce dotazu. To znamená, že pokud již instance `Customer`ho typu v <xref:System.Data.Services.Client.DataServiceContext>existuje, bude instance `CustomerAddress` se stejnou identitou dodržovat pravidla překladu identit nastavená <xref:System.Data.Services.Client.MergeOption>

Následující článek popisuje chování při projekci výsledků do entit a typů bez entit:

**Vytvoření nové plánované instance pomocí inicializátorů**

- Příklad:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- Typ entity: podporováno

- Typ, který není entitou: podporováno

**Vytvoření nové projektové instance pomocí konstruktorů**

- Příklad:

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- Typ entity: je vyvolána <xref:System.NotSupportedException>.

- Typ, který není entitou: podporováno

**Transformace hodnoty vlastnosti pomocí projekce**

- Příklad:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- Typ entity: Tato transformace není u typů entit podporovaná, protože může vést k nejasnostem a potenciálně přepsat data ve zdroji dat, který patří do jiné entity. Je vyvolána <xref:System.NotSupportedException>.

- Typ, který není entitou: podporováno

<a name="considerations"></a>

## <a name="projection-considerations"></a>Posouzení projekce

Při definování projekce dotazu platí následující další požadavky.

- Když definujete vlastní kanály pro formát Atom, musíte se ujistit, že všechny vlastnosti entity, které mají definované vlastní mapování, jsou zahrnuté do projekce. Pokud v projekci není obsažena vlastnost mapované entity, může dojít ke ztrátě dat. Další informace najdete v tématu [přizpůsobení informačního kanálu](feed-customization-wcf-data-services.md).

- Když jsou vloženy do projektového typu, který neobsahuje všechny vlastnosti entity v datovém modelu datové služby, vlastnosti nezahrnuté do projekce v klientovi jsou nastaveny na výchozí hodnoty.

- Když se provedou aktualizace na základě předpokládaného typu, který neobsahuje všechny vlastnosti entity v datovém modelu datové služby, existující hodnoty, které nejsou zahrnuté do projekce na straně klienta, budou přepsány neinicializovanými výchozími hodnotami.

- Pokud projekce obsahuje komplexní vlastnost, musí být vrácen celý komplexní objekt.

- Pokud projekce obsahuje navigační vlastnost, související objekty jsou načteny implicitně bez nutnosti volat metodu <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>. Metoda <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> není podporována pro použití v projektovém dotazu.

- Dotazy na projekce dotazů na klientovi se překládají na použití možnosti dotaz `$select` v identifikátoru URI požadavku. Když se dotaz se projekcí provede v předchozí verzi WCF Data Services, která nepodporuje možnost dotazu `$select`, vrátí se chyba. K tomu může dojít také v případě, že je <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> <xref:System.Data.Services.DataServiceBehavior> datové služby nastaveno na hodnotu <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Další informace najdete v tématu [Správa verzí datových služeb](data-service-versioning-wcf-data-services.md).

Další informace najdete v tématu [Postup: výsledky dotazu na projekt](how-to-project-query-results-wcf-data-services.md).

## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
