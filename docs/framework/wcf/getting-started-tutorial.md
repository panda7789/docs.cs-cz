---
title: Začínáme se službou Tutorial1
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: e5a07e5264c715f568121403721a3c844b903d99
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085659"
---
# <a name="getting-started-tutorial"></a>Kurz Začínáme
Témata obsažené v této části jsou určeny umožňují rychlé odhalení pro Windows Communication Foundation (WCF) programovací prostředí. Jsou navrženy dokončit v pořadí podle seznamu v dolní části tohoto tématu. Absolvování tohoto kurzu pochopíte úvodní kroky potřebné k vytváření služeb WCF a klientských aplikací. Služba zpřístupňuje jeden nebo více koncových bodů, každý z nich vystavuje jednu nebo víc operací služeb. *Koncový bod* služby určuje adresu, kde najdete službu, vazbu, která obsahuje informace, které popisuje, jak klient musí komunikovat s službu a kontrakt, který definuje funkce poskytovaných službou svým klientům.  
  
 Po dokončení řady témat v tomto kurzu, budete mít funkční službu a klient zavolá službu. První tři témata popisují definování kontraktu služby, implementace kontraktu služby a jak pro hostování služby. Vytvořená služba je v rámci konzolové aplikace v místním prostředí. Služby mohou být také hostovány v rámci Internetové informační služby (IIS). Další informace o tom, jak to provést, najdete v části [postupy: hostování služby WCF v IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md). Služba je nakonfigurována v kódu; služba však lze také nastavit v konfiguračním souboru. Další informace o použití konfiguračního souboru naleznete v tématu [konfigurace služeb pomocí konfiguračních souborů](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).  
  
 Následující tři tématech najdete popis postupu vytvoření proxy serveru klienta, konfigurovat klientskou aplikaci a používat proxy server klienta k volání operace služby, vystavený službou. Služby publikování metadat, které definují informace, které klientská aplikace potřebuje ke komunikaci se službou. [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] automatizuje proces přístup k tato metadata a použije ho k vytvořit a konfigurovat klientskou aplikaci pro službu. Pokud nepoužíváte [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], můžete použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vytvořit a konfigurovat klientskou aplikaci pro službu.  
  
 Všechna témata v této části se předpokládá, že používáte jako vývojové prostředí sady Visual Studio 2011. Pokud používáte jiné vývojové prostředí, ignorujte konkrétní pokyny sady Visual Studio.  
  
> [!NOTE]
>  Pokud používáte [!INCLUDE[wv](../../../includes/wv-md.md)] nebo novější verze operačního systému Windows, musíte spustit aplikaci Visual Studio do nabídky Start a Visual Studio 2011 kliknutím pravým tlačítkem myši a vybrat možnost **spustit jako správce**. Vždy spustit Visual Studio 2011 jako správce můžete vytvořit místní, klikněte pravým tlačítkem myši místní, vyberte vlastnosti, vyberte **kompatibility** kartu a podívejte se **spustit tento program jako správce** zaškrtávací políčko. Při spuštění sady Visual Studio 2011 s touto klávesovou bude vždy spustit jako správce.  
  
 Pro ukázkové aplikace, které lze stáhnout na pevný disk a spouštět, najdete v tématech [ukázky Windows Communication Foundation](https://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91). Pro toto téma, najdete v tématu, zejména v případě, [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
 Další podrobné informace o vytváření služeb a klientů najdete v tématu [základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 Popisuje postup vytvoření kontraktu WCF pomocí uživatelského rozhraní. Kontrakt definuje funkci určeného službou.  
  
 [Postupy: Implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 Popisuje způsob implementace kontraktu služby. Jakmile kontrakt definovat, musí být implementované pomocí třídy service.  
  
 [Postupy: Hostování a spuštění základní služby](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 Popisuje postup konfigurace koncového bodu služby v kódu a hostovat službu v konzolové aplikaci. Aktivuje, musí být nakonfigurované služby a hostované v rámci prostředí za běhu. Toto prostředí vytvoří službu a ovládací prvky jeho kontextu a životnosti.  
  
 [Postupy: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 Popisuje, jak načíst metadata použitý k vytvoření proxy serveru klienta WCF na službu WCF. Tento proces používá funkci Přidat odkaz na službu v rámci sady Visual Studio 2011.  
  
 [Postupy: Konfigurace klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 Popisuje postup konfigurace WCF klienta Konfigurace klienta vyžaduje zadání koncového bodu, který klient používá pro přístup ke službě.  
  
 [Postupy: Používání klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 Popisuje způsob použití proxy serveru klienta WCF k vyvolání operace služby.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## <a name="related-sections"></a>Související oddíly  
 [Ukázky Windows Communication Foundation](https://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [Základní programovací životní cyklus](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepční přehled](../../../docs/framework/wcf/conceptual-overview.md)  
 [Průvodce dokumentací](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Co je Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Podrobnosti o funkcích WCF](../../../docs/framework/wcf/feature-details/index.md)
