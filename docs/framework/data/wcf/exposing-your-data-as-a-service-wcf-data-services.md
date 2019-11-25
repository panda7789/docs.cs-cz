---
title: Zpřístupnění dat jako služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 71f26d7d41d112e13e6a77f0927c61d51b176b27
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975312"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Vystavení dat jako služby (WCF Data Services)

WCF Data Services se integruje se sadou Visual Studio, aby bylo možné snadněji definovat služby, které budou zveřejňovat vaše data jako informační kanály OData (Open Data Protocol). Vytvoření datové služby, která zveřejňuje datový kanál OData, zahrnuje následující základní kroky:

1. **Definujte datový model.** WCF Data Services nativně podporuje datové modely založené na [Entity Framework ADO.NET](../adonet/ef/index.md). Další informace najdete v tématu [Postupy: vytvoření datové služby pomocí Entity Framework zdroje dat v ADO.NET](create-a-data-service-using-an-adonet-ef-data-wcf.md).

     WCF Data Services podporuje také datové modely založené na objektech CLR (Common Language Runtime), které vracejí instanci rozhraní <xref:System.Linq.IQueryable%601>. To umožňuje nasazení datových služeb založených na seznamech, polích a kolekcích v .NET Framework. Chcete-li povolit operace vytváření, aktualizace a odstraňování v těchto datových strukturách, je nutné také implementovat rozhraní <xref:System.Data.Services.IUpdatable>. Další informace najdete v tématu [Postupy: vytvoření datové služby pomocí poskytovatele reflexe](create-a-data-service-using-rp-wcf-data-services.md).

     Pro pokročilejší scénáře WCF Data Services obsahuje sadu zprostředkovatelů, které vám umožní definovat datový model na základě datových typů s pozdní vazbou. Další informace najdete v tématu [Vlastní poskytovatelé datových služeb](custom-data-service-providers-wcf-data-services.md).

2. **Vytvořte datovou službu.** Většina základních datových služeb zpřístupňuje třídu, která dědí z třídy <xref:System.Data.Services.DataService%601>, s typem `T`, který je kvalifikovaný název oboru názvů kontejneru entit. Další informace najdete v tématu [definování WCF Data Services](defining-wcf-data-services.md).

3. **Nakonfigurujte datovou službu.** Ve výchozím nastavení WCF Data Services zakáže přístup k prostředkům, které jsou zpřístupněny kontejnerem entit. Rozhraní <xref:System.Data.Services.DataServiceConfiguration> umožňuje nakonfigurovat přístup k prostředkům a operacím služby, určit podporovanou verzi OData a definovat další chování v rámci služby, jako je například chování dávkování nebo maximální počet entit, které mohou být vráceny v rámci jedné odpovědi. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).

Příklad toho, jak vytvořit jednoduchou datovou službu založenou na ukázkové databázi Northwind, najdete v tématu [rychlý Start](quickstart-wcf-data-services.md).

## <a name="see-also"></a>Viz také:

- [Začínáme](getting-started-with-wcf-data-services.md)
- [Přehled](wcf-data-services-overview.md)
