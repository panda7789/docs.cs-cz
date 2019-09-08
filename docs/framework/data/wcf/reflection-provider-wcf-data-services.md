---
title: Zprostředkovatel reflexe (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: c3e160f96be2a95262776994152a06b42b475887
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779803"
---
# <a name="reflection-provider-wcf-data-services"></a>Zprostředkovatel reflexe (WCF Data Services)

Kromě vystavení dat z datového modelu prostřednictvím Entity Framework [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] může vystavovat data, která nejsou definovaná v modelu založeném na entitách. Zprostředkovatel reflexe zpřístupňuje data ve třídách, které vracejí <xref:System.Linq.IQueryable%601> typy, které implementují rozhraní. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]používá reflexi k odvození datového modelu pro tyto třídy a může překládat dotazy založené na adresách na prostředky do dotazů založených na jazyce LINQ (Language <xref:System.Linq.IQueryable%601> Integrated Query) na vystavených typech.

> [!NOTE]
> <xref:System.Linq.Queryable.AsQueryable%2A> Metodu můžete použít k <xref:System.Linq.IQueryable%601> vrácení rozhraní z <xref:System.Collections.Generic.IEnumerable%601> libovolné třídy, která implementuje rozhraní. To umožňuje použití většiny obecných typů kolekcí jako zdroje dat pro datovou službu.

Zprostředkovatel reflexe podporuje hierarchie typů. Další informace najdete v tématu [jak: Vytvořte datovou službu pomocí poskytovatele](create-a-data-service-using-rp-wcf-data-services.md)reflexe.

## <a name="inferring-the-data-model"></a>Odvození datového modelu

Když vytvoříte datovou službu, zprostředkovatel odvodí datový model pomocí reflexe. Následující seznam ukazuje, jak poskytovatel reflexe odvodí datový model:

- Kontejner entity – třída, která zpřístupňuje data jako vlastnosti, které vracejí <xref:System.Linq.IQueryable%601> instanci. Když řešíte datový model založený na reflexi, kontejner entity představuje kořen služby. Pro daný obor názvů je podporována pouze jedna třída kontejneru entity.

- Sady entit – vlastnosti, které <xref:System.Linq.IQueryable%601> vracejí instance, se považují za sady entit. Sady entit jsou řešeny přímo jako prostředky v dotazu. <xref:System.Linq.IQueryable%601> Instance daného typu může vracet pouze jedna vlastnost kontejneru entity.

- Typy entit – typ `T` <xref:System.Linq.IQueryable%601> , který sada entit vrátí. Třídy, které jsou součástí hierarchie dědičnosti, jsou přeloženy poskytovatelem reflexe do ekvivalentní hierarchie typů entit.

- Klíče entit – každá třída dat, která je typem entity, musí mít vlastnost Key. Tato vlastnost je označena <xref:System.Data.Services.Common.DataServiceKeyAttribute> atributem (`[DataServiceKeyAttribute]`).

    > [!NOTE]
    > <xref:System.Data.Services.Common.DataServiceKeyAttribute> Atribut byste měli použít pouze pro vlastnost, která může být použita k jednoznačné identifikaci instance typu entity. Tento atribut je ignorován při použití pro navigační vlastnost.

- Vlastnosti typu entity – jiné než klíč entity, považuje poskytovatel reflexe přístupné, neindexerové vlastnosti třídy, která je typu entity, takto:

  - Pokud vlastnost vrací primitivní typ, pak je vlastnost považována za vlastnost typu entity.

  - Pokud vlastnost vrátí typ, který je také typem entity, pak je vlastnost považována za navigační vlastnost, která představuje "jeden" konec vztahu 1:1 nebo 1:1.

  - Pokud vlastnost vrátí <xref:System.Collections.Generic.IEnumerable%601> typ entity, pak je vlastnost považována za navigační vlastnost, která představuje "mnoho" na konci relace 1: n nebo m:n.

  - Pokud návratový typ vlastnosti je typ hodnoty, pak vlastnost představuje komplexní typ.

> [!NOTE]
> Na rozdíl od datového modelu, který je založen na relačním modelu entity, modely založené na zprostředkovateli reflexe nerozumí relačním datům. K vystavení relačních dat prostřednictvím [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nástroje byste měli použít Entity Framework.

## <a name="data-type-mapping"></a>Mapování datových typů

Pokud je datový model odvozen z .NET Framework třídy, jsou primitivní typy v datovém modelu namapovány na .NET Framework datové typy takto:

|.NET Framework datový typ|Typ datového modelu|
|------------------------------|---------------------|
|<xref:System.Byte>`[]`|`Edm.Binary`|
|<xref:System.Boolean>|`Edm.Boolean`|
|<xref:System.Byte>|`Edm.Byte`|
|<xref:System.DateTime>|`Edm.DateTime`|
|<xref:System.Decimal>|`Edm.Decimal`|
|<xref:System.Double>|`Edm.Double`|
|<xref:System.Guid>|`Edm.Guid`|
|<xref:System.Int16>|`Edm.Int16`|
|<xref:System.Int32>|`Edm.Int32`|
|<xref:System.Int64>|`Edm.Int64`|
|<xref:System.SByte>|`Edm.SByte`|
|<xref:System.Single>|`Edm.Single`|
|<xref:System.String>|`Edm.String`|

> [!NOTE]
> .NET Framework typy hodnot s možnou hodnotou null jsou mapovány na stejné typy datových modelů jako odpovídající typy hodnot, které nemohou být přiřazeny hodnotě null.

## <a name="enabling-updates-in-the-data-model"></a>Povolení aktualizací v datovém modelu

Aby bylo možné zajistit aktualizace dat, která jsou zveřejněna prostřednictvím tohoto druhu datového modelu, Zprostředkovatel reflexe <xref:System.Data.Services.IUpdatable> definuje rozhraní. Toto rozhraní instruuje datovou službu o tom, jak uchovat aktualizace vystavených typů. Aby bylo možné povolit aktualizace prostředků, které jsou definovány datovým modelem, třída kontejneru entity musí implementovat <xref:System.Data.Services.IUpdatable> rozhraní. Příklad implementace <xref:System.Data.Services.IUpdatable> rozhraní naleznete v tématu [How to: Vytvořte datovou službu pomocí LINQ to SQL zdroje](create-a-data-service-using-linq-to-sql-wcf.md)dat.

<xref:System.Data.Services.IUpdatable> Rozhraní vyžaduje, aby následující členové byli implementováni, aby bylo možné aktualizace rozšířit na zdroj dat pomocí poskytovatele reflexe:

|Člen|Popis|
|------------|-----------------|
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Poskytuje funkce pro přidání objektu do kolekce souvisejících objektů, které jsou k dispozici z navigační vlastnosti.|
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Poskytuje funkce, které zruší probíhající změny dat.|
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Poskytuje funkce pro vytvoření nového prostředku v zadaném kontejneru.|
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Poskytuje funkce pro odstranění prostředku.|
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Poskytuje funkce pro načtení prostředku, který je identifikován konkrétním dotazem a názvem typu.|
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Poskytuje funkce pro návrat hodnoty vlastnosti prostředku.|
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Poskytuje funkce pro odebrání objektu na kolekci souvisejících objektů, ke kterým se přistupovala z navigační vlastnosti.|
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Poskytuje funkce pro aktualizaci zadaného prostředku.|
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Poskytuje funkce pro vrácení prostředku, který je reprezentován konkrétní instancí objektu.|
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Poskytuje funkce pro uložení všech nedokončených změn.|
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Poskytuje funkce pro nastavení souvisejícího odkazu na objekt pomocí navigační vlastnosti.|
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Poskytuje funkce pro nastavení hodnoty vlastnosti prostředku.|

## <a name="handling-concurrency"></a>Ošetření souběžnosti

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]podporuje optimistický model souběžnosti tím, že umožňuje definovat Token souběžnosti pro entitu. Tento token souběžnosti, který obsahuje jednu nebo více vlastností entity, používá datová služba k určení, zda došlo ke změně v datech, která jsou požadována, aktualizována nebo odstraněna. Pokud se hodnoty tokenu získané z eTag v požadavku liší od aktuální hodnoty entity, vyvolá datová služba výjimku. <xref:System.Data.Services.ETagAttribute> Je použita na typ entity k definování tokenu souběžnosti v poskytovateli reflexe. Token souběžnosti nemůže obsahovat vlastnost klíče ani navigační vlastnost. Další informace najdete v tématu [aktualizace datové služby](updating-the-data-service-wcf-data-services.md).

## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Použití LINQ to SQL se zprostředkovatelem reflexe

Vzhledem k tomu, že Entity Framework je nativně podporován ve výchozím nastavení, je doporučeným poskytovatelem dat pro [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]použití relačních dat s. Můžete však použít poskytovatele reflexe k použití třídy LINQ to SQL s datovou službou. Sady výsledků, které jsou vráceny metodami <xref:System.Data.Linq.DataContext> vygenerovanými LINQ to SQL Návrhář relací objektů (Návrhář O/ <xref:System.Linq.IQueryable%601> R) implementují rozhraní. <xref:System.Data.Linq.Table%601> To umožňuje poskytovateli reflexi přistupovat k těmto metodám a vracet data entit z SQL Server pomocí generovaných LINQ to SQL tříd. Protože však LINQ to SQL neimplementuje <xref:System.Data.Services.IUpdatable> rozhraní, je nutné přidat částečnou třídu, která rozšiřuje existující <xref:System.Data.Linq.DataContext> <xref:System.Data.Services.IUpdatable> částečnou třídu pro přidání implementace. Další informace najdete v tématu [jak: Vytvořte datovou službu pomocí LINQ to SQL zdroje](create-a-data-service-using-linq-to-sql-wcf.md)dat.

## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
