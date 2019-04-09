---
title: Zprostředkovatel reflexe (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: e36f9124ec9979dac69b596c6d87491581ae9ec6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159520"
---
# <a name="reflection-provider-wcf-data-services"></a>Zprostředkovatel reflexe (WCF Data Services)
Kromě úniku dat z datového modelu pomocí Entity Framework [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] můžete zpřístupnit data, která není striktně definované v modelu na základě entity. Zprostředkovatel reflexe zveřejňuje data v třídách, které vrací typy, které implementují <xref:System.Linq.IQueryable%601> rozhraní. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] používá reflexi k odvození datový model pro tyto třídy a jsou dobře převeditelné na základě adres dotazy na prostředky do jazyka integrované dotazu (LINQ) – na základě dotazů vystavené <xref:System.Linq.IQueryable%601> typy.  
  
> [!NOTE]
>  Můžete použít <xref:System.Linq.Queryable.AsQueryable%2A> metodu pro návrat <xref:System.Linq.IQueryable%601> rozhraní z jiné třídy, která implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní. To umožňuje nejvíce obecných typů kolekce použitého jako zdroj dat pro datové služby.  
  
 Zprostředkovatel reflexe podporuje hierarchie typů. Další informace najdete v tématu [jak: Vytvoření datové služby pomocí zprostředkovatel reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
## <a name="inferring-the-data-model"></a>Odvození datového modelu  
 Při vytváření datové služby poskytovatele odvodí datového modelu pomocí reflexe. Následující seznam ukazuje, jak se zprostředkovatel reflexe odvodí datového modelu:  
  
-   Kontejner entit – třída, která zveřejňuje data jako vlastnosti, které vracejí <xref:System.Linq.IQueryable%601> instance. Při adresování založenými na reflexi datový model kontejneru entity reprezentuje kořen služby. Pro daný obor názvů je podporována pouze jedna entita kontejner – třída.  
  
-   Sady entit – vlastnosti, které vracejí <xref:System.Linq.IQueryable%601> instancí jsou považovány za sady entit. Sady entit se tak vyřeší přímo jako prostředky v dotazu. Může vrátit pouze jedna vlastnost v kontejneru entity <xref:System.Linq.IQueryable%601> instance daného typu.  
  
-   Typy entit – typ `T` z <xref:System.Linq.IQueryable%601> , sady entit vrátí. Třídy, které jsou součástí hierarchie dědičnosti se přeložit poskytovatelem reflexe do hierarchie typu ekvivalentní entit.  
  
-   Klíče entit – každý data třídy, která je typ entity musí mít vlastnost klíče. Tato vlastnost má atribut <xref:System.Data.Services.Common.DataServiceKeyAttribute> atribut (`[DataServiceKeyAttribute]`).  
  
    > [!NOTE]
    >  Byste měli použít pouze <xref:System.Data.Services.Common.DataServiceKeyAttribute> atributu na vlastnost, která slouží k jednoznačné identifikaci instance typu entity. Tento atribut se ignoruje, když použitý pro navigační vlastnost.  
  
-   Vlastnosti typu entity - jiné než klíč entity, zprostředkovatel reflexe zpracovává přístupné, bez indexeru vlastnosti třídy, která je typ entity následujícím způsobem:  
  
    -   Pokud vlastnost vrátí primitivní typ, se předpokládá vlastnost jako vlastnost typu entity.  
  
    -   Pokud vlastnost vrátí typ, který je také typ entity, se předpokládá vlastnost jako vlastnost navigace, který představuje "jedna" Konec relace m: 1 nebo 1: 1.  
  
    -   Pokud vlastnost vrátí <xref:System.Collections.Generic.IEnumerable%601> typu entity, pak vlastnost je považován za navigační vlastnost, která představuje "řada" konec vztah jeden mnoho nebo many-to-many.  
  
    -   Pokud návratový typ vlastnosti je hodnotový typ, vlastnost představuje komplexního typu.  
  
> [!NOTE]
>  Na rozdíl od datový model, který je založen na entity relačního modelu modely, které jsou založeny na zprostředkovatel reflexe není srozumitelný relační data. Entity Framework by měl používat ke zveřejňování relačních dat prostřednictvím [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
## <a name="data-type-mapping"></a>Mapování datového typu  
 Pokud datový model je odvozen z třídy rozhraní .NET Framework, primitivní typy v datovém modelu namapované na datové typy rozhraní .NET Framework následujícím způsobem:  
  
|Datový typ rozhraní .NET framework|Typ datového modelu|  
|------------------------------|---------------------|  
|<xref:System.Byte> `[]`|`Edm.Binary`|  
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
>  Typy s možnou hodnotou Null v rozhraní .NET framework jsou namapovány na stejný model datové typy jako odpovídající typy hodnot, které nelze přiřadit hodnotu null.  
  
## <a name="enabling-updates-in-the-data-model"></a>Povolení aktualizací v datovém modelu  
 Pokud chcete povolit aktualizace dat, která je k dispozici prostřednictvím tento druh datového modelu, zprostředkovatel reflexe definuje <xref:System.Data.Services.IUpdatable> rozhraní. Toto rozhraní nastaví službu dat o tom, jak zachovat aktualizace vystavené typy. Pokud chcete povolit aktualizací pro prostředky, které jsou definovány datový model, musí implementovat třídu kontejneru entity <xref:System.Data.Services.IUpdatable> rozhraní. Příklad implementace <xref:System.Data.Services.IUpdatable> rozhraní najdete v tématu [jak: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 <xref:System.Data.Services.IUpdatable> Rozhraní vyžaduje, aby aktualizace mohou být přeneseny do zdroje dat pomocí zprostředkovatel reflexe implementovat následující členy:  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Poskytuje funkce pro přidání objektu do kolekce souvisejících objektů, které jsou přístupné z navigační vlastnost.|  
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Poskytuje funkce, které ruší čekající změny v datech.|  
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Poskytuje funkce pro vytvoření nového prostředku v zadaném kontejneru.|  
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Poskytuje funkce pro odstranění prostředku.|  
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Poskytuje funkce pro načtení prostředku, který je identifikován podle konkrétního názvu dotazu a typu.|  
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Poskytuje funkci, která vrátí hodnotu vlastnosti prostředku.|  
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Poskytuje funkce pro odstranění objektu na kolekci souvisejících objektů, které jsou k němu přistupovat z navigační vlastnost.|  
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Poskytuje funkce se aktualizovat zadaný prostředek.|  
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Poskytuje funkce pro prostředek, která je reprezentována instance určitého objektu.|  
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Poskytuje funkce pro uložit všechny neuložené změny.|  
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Poskytuje funkce pro nastavení odkaz na objekt v relaci s použitím navigační vlastnost.|  
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Poskytuje funkce pro nastavení hodnoty vlastnosti prostředku.|  
  
## <a name="handling-concurrency"></a>Ošetření souběžnosti  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje model pomocí optimistického řízení souběžnosti tím, že vám k definování tokenem souběžnosti pro entitu. Tento token souběžnosti, který obsahuje jednu nebo více vlastností entity, používá k určení, zda došlo ke změně v datech, které jsou požadovány, aktualizovaných nebo odstraněných datové služby. Když token hodnoty získané ze značky eTag v požadavku se liší od aktuální hodnoty entity, je vyvolána výjimka datovou službou. <xref:System.Data.Services.ETagAttribute> Platí pro typ entity k definování tokenem souběžnosti v zprostředkovatel reflexe. Tokenem souběžnosti není možné zahrnout klíčová vlastnost nebo vlastnost navigace. Další informace najdete v tématu [aktualizace datové služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Technologie LINQ to SQL pomocí zprostředkovatel reflexe  
 Vzhledem k tomu, že ve výchozím nastavení je nativně podporuje rozhraní Entity Framework, je poskytovatel dat doporučené pro použití s relačními daty [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Můžete však použít zprostředkovatel reflexe použití LINQ na třídy SQL se službou data. <xref:System.Data.Linq.Table%601> Sady, které jsou vráceny pomocí jiných metod na výsledků <xref:System.Data.Linq.DataContext> vygenerován pomocí LINQ to SQL Návrhář relací objektů (O/R Designer) implementace <xref:System.Linq.IQueryable%601> rozhraní. To umožňuje zprostředkovatel reflexe pro přístup k tyto metody a vrátí entity data z SQL serveru pomocí generovaného LINQ na třídy SQL. Ale protože technologie LINQ to SQL neimplementuje <xref:System.Data.Services.IUpdatable> rozhraní, je třeba přidat dílčí třídy, které rozšiřuje existující <xref:System.Data.Linq.DataContext> částečné třídy pro přidání <xref:System.Data.Services.IUpdatable> implementace. Další informace najdete v tématu [jak: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
