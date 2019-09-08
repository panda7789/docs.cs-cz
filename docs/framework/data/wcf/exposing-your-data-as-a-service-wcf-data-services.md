---
title: Zpřístupnění dat jako služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 1dc1f0ec12c50c4c97b141a34b468e3367ead75e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780297"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Vystavení dat jako služby (WCF Data Services)

WCF Data Services se integruje se sadou Visual Studio, aby bylo možné snadněji definovat služby, které zpřístupňují [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] vaše data jako informační kanály. Vytvoření datové služby, která zveřejňuje datový kanál OData, zahrnuje následující základní kroky:

1. **Definujte datový model.** WCF Data Services nativně podporuje datové modely založené na [Entity Framework ADO.NET](../adonet/ef/index.md). Další informace najdete v tématu [jak: Vytvořte datovou službu pomocí Entity Framework zdroje](create-a-data-service-using-an-adonet-ef-data-wcf.md)dat ADO.NET.

     WCF Data Services také podporuje datové modely založené na objektech CLR (Common Language Runtime), které vracejí instanci <xref:System.Linq.IQueryable%601> rozhraní. To umožňuje nasazení datových služeb založených na seznamech, polích a kolekcích v .NET Framework. Chcete-li povolit operace vytváření, aktualizace a odstraňování v těchto datových strukturách, je nutné také <xref:System.Data.Services.IUpdatable> implementovat rozhraní. Další informace najdete v tématu [jak: Vytvořte datovou službu pomocí poskytovatele](create-a-data-service-using-rp-wcf-data-services.md)reflexe.

     Pro pokročilejší scénáře WCF Data Services obsahuje sadu zprostředkovatelů, které vám umožní definovat datový model na základě datových typů s pozdní vazbou. Další informace najdete v tématu [Vlastní poskytovatelé datových služeb](custom-data-service-providers-wcf-data-services.md).

2. **Vytvořte datovou službu.** Většina základních datových služeb zpřístupňuje třídu, která dědí z <xref:System.Data.Services.DataService%601> třídy, s typem `T` , který je kvalifikovaný název oboru názvů kontejneru entit. Další informace najdete v tématu [definování WCF Data Services](defining-wcf-data-services.md).

3. **Nakonfigurujte datovou službu.** Ve výchozím nastavení WCF Data Services zakáže přístup k prostředkům, které jsou zpřístupněny kontejnerem entit. <xref:System.Data.Services.DataServiceConfiguration> Rozhraní umožňuje nakonfigurovat přístup k prostředkům a operacím služby, určit podporovanou verzi OData a definovat další chování v rámci služby, například chování dávkování nebo maximální počet entit, které mohou být vráceny. v jediné odpovědi. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).

Příklad toho, jak vytvořit jednoduchou datovou službu založenou na ukázkové databázi Northwind, najdete v tématu [rychlý Start](quickstart-wcf-data-services.md).

## <a name="see-also"></a>Viz také:

- [Začínáme](getting-started-with-wcf-data-services.md)
- [Přehled](wcf-data-services-overview.md)
