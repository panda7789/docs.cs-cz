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
ms.openlocfilehash: 44e99db2d75fcd8e84f91f0afc8da54ff6c3f707
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931168"
---
# <a name="query-projections-wcf-data-services"></a>Projekce dotazů (WCF Data Services)

Projekce poskytuje mechanizmus [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pro snížení objemu dat v informačním kanálu vrácených dotazem zadáním, že v odpovědi jsou vráceny pouze některé vlastnosti entity. Další informace najdete v tématu [OData: Vyberte možnost dotaz na systém ($select](https://go.microsoft.com/fwlink/?LinkId=186076)).

Toto téma popisuje, jak definovat projekci dotazu, jaké jsou požadavky pro entity a typy bez entit, které provádějí aktualizace s plánovanými výsledky, vytváření projektových typů a uvádí některé informace o projekci.

## <a name="defining-a-query-projection"></a>Definování projekce dotazu

Klauzuli projekce můžete k dotazu přidat buď pomocí `$select` možnosti dotazu v identifikátoru URI, nebo pomocí klauzule [Select](../../../csharp/language-reference/keywords/select-clause.md) ([Select](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) v dotazu LINQ. Vrácená data entity lze v klientovi promítnout buď na typy entit, nebo na typy bez entit. Příklady v tomto tématu ukazují, jak použít `select` klauzuli v dotazu LINQ.

> [!IMPORTANT]
> Při ukládání aktualizací, které byly provedeny s plánovanými typy, může dojít ke ztrátě dat v datové službě. Další informace najdete v tématu [](#considerations)věnovaném projekčním hlediskům.

## <a name="requirements-for-entity-and-non-entity-types"></a>Požadavky na typy entit a jiných entit

Typy entit musí mít jednu nebo více vlastností identity, které tvoří klíč entity. Typy entit jsou definovány v klientech jedním z následujících způsobů:

- <xref:System.Data.Services.Common.DataServiceKeyAttribute> Použitím nebo <xref:System.Data.Services.Common.DataServiceEntityAttribute> na typ.

- Když typ obsahuje vlastnost s názvem `ID`.

- Když typ obsahuje vlastnost s názvem *Type*`ID`, kde *Type* je název typu.

Ve výchozím nastavení se při dotazování výsledků dotazu na typ definovaný v klientovi musí v typu klienta vyskytovat vlastnosti požadované v projekci. Pokud však zadáte hodnotu `true` <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> pro vlastnost <xref:System.Data.Services.Client.DataServiceContext>, vlastnosti zadané v projekci nejsou požadovány pro výskyt v typu klienta.

### <a name="making-updates-to-projected-results"></a>Provádění aktualizací s plánovanými výsledky

Při dotazování výsledků dotazu na typy entit v klientovi <xref:System.Data.Services.Client.DataServiceContext> může aplikace sledovat tyto objekty s aktualizacemi, které se mají odeslat zpět do datové služby <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> při volání metody. Aktualizace provedené v datech, které se procházejí na typy neentitované v klientovi, se ale nedají poslat zpátky do datové služby. Důvodem je to, že bez klíče k identifikaci instance entity nemůže datová služba aktualizovat správnou entitu ve zdroji dat. Typy, které nejsou entitou, nejsou připojeny <xref:System.Data.Services.Client.DataServiceContext>k.

V případě, že jedna nebo více vlastností typu entity definovaného v datové službě se neobjeví v typu klienta, do kterého je entita provedená, vkládání nových entit nebudou obsahovat tyto chybějící vlastnosti. V takovém případě nebudou aktualizace provedené u stávajících entit obsahovat **také** tyto chybějící vlastnosti. Pokud pro takovou vlastnost existuje hodnota, aktualizace ji obnoví na výchozí hodnotu vlastnosti, jak je definováno ve zdroji dat.

### <a name="creating-projected-types"></a>Vytváření projektových typů

V následujícím příkladu je použit anonymní dotaz LINQ, který projektuje vlastnosti `Customers` související s adresou typu do nového `CustomerAddress` typu, který je definován v klientovi a má atribut jako typ entity:

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

V tomto příkladu je použit vzor inicializátoru objektu k vytvoření nové instance `CustomerAddress` typu namísto volání konstruktoru. Konstruktory nejsou podporovány při projekci do typů entit, ale lze je použít při projekci na jiné než entity a anonymní typy. Vzhledem `CustomerAddress` k tomu, že je typ entity, lze provádět změny a odesílat je zpět do datové služby.

Data z tohoto `Customer` typu se také prochází do instance `CustomerAddress` typu entity namísto anonymního typu. Projekce na anonymní typy je podporována, ale data jsou jen pro čtení, protože anonymní typy jsou považovány za typy bez entit.

<xref:System.Data.Services.Client.MergeOption> Nastavení ,<xref:System.Data.Services.Client.DataServiceContext> které se používá pro překlad identity během projekce dotazu. To znamená, že pokud instance `Customer` typu již v rozhraní <xref:System.Data.Services.Client.DataServiceContext>existuje, bude instance `CustomerAddress` se stejnou identitou dodržovat pravidla překladu identit nastavená<xref:System.Data.Services.Client.MergeOption>

Následující článek popisuje chování při projekci výsledků do entit a typů bez entit:

**Vytvoření nové plánované instance pomocí inicializátorů**

- Příklad:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- Typ entity: Podporováno

- Typ, který není entitou: Podporováno

**Vytvoření nové projektové instance pomocí konstruktorů**

- Příklad:

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- Typ entity: <xref:System.NotSupportedException> Je vyvolána výjimka.

- Typ, který není entitou: Podporováno

**Transformace hodnoty vlastnosti pomocí projekce**

- Příklad:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- Typ entity: Tato transformace není u typů entit podporovaná, protože může vést k nejasnostem a potenciálně přepsat data ve zdroji dat, který patří do jiné entity. <xref:System.NotSupportedException> Je vyvolána výjimka.

- Typ, který není entitou: Podporováno

<a name="considerations"></a>

## <a name="projection-considerations"></a>Posouzení projekce

Při definování projekce dotazu platí následující další požadavky.

- Když definujete vlastní kanály pro formát Atom, musíte se ujistit, že všechny vlastnosti entity, které mají definované vlastní mapování, jsou zahrnuté do projekce. Pokud v projekci není obsažena vlastnost mapované entity, může dojít ke ztrátě dat. Další informace najdete v tématu [přizpůsobení informačního kanálu](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).

- Když jsou vloženy do projektového typu, který neobsahuje všechny vlastnosti entity v datovém modelu datové služby, vlastnosti nezahrnuté do projekce v klientovi jsou nastaveny na výchozí hodnoty.

- Když se provedou aktualizace na základě předpokládaného typu, který neobsahuje všechny vlastnosti entity v datovém modelu datové služby, existující hodnoty, které nejsou zahrnuté do projekce na straně klienta, budou přepsány neinicializovanými výchozími hodnotami.

- Pokud projekce obsahuje komplexní vlastnost, musí být vrácen celý komplexní objekt.

- Pokud projekce obsahuje navigační vlastnost, související objekty jsou načteny implicitně bez nutnosti volání <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Metoda není podporována pro použití v projektovém dotazu.

- Dotazy na projekce dotazů na klientovi se překládají na použití `$select` možnosti dotazu v identifikátoru URI požadavku. Když se dotaz se projekcí provede v předchozí verzi [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] nástroje, která `$select` nepodporuje možnost dotaz, vrátí se chyba. K tomu může dojít také v <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> případě <xref:System.Data.Services.DataServiceBehavior> , že je služba pro datovou službu <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>nastavena na hodnotu. Další informace najdete v tématu [Správa verzí datových služeb](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).

Další informace najdete v tématu [jak: Výsledky](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)dotazu projektu.

## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
