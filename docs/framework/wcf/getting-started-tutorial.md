---
title: Začínáme Tutorial1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
caps.latest.revision: 47
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c66e7d8f610126e2702a6c593a93ee496108ecf
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="getting-started-tutorial"></a>Kurz Začínáme
Témata obsažené v této části jsou určeny tak, abyste získali rychlý vystavení [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] programovací prostředí. Jsou navrženy dokončit v pořadí podle seznamu v dolní části tohoto tématu. Absolvování tohoto kurzu pochopíte úvodní kroky potřebné k vytvoření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby a klientské aplikace. Služba vystavuje jeden nebo více koncových bodů, každý z nich vystavuje jednu nebo víc operací služeb. *Koncový bod* služby specifikuje adresu, kde můžete najít službu, vazbu, která obsahuje informace, které popisují, jak klient musí komunikovat s službu a kontrakt, který definuje funkci poskytovaný službou svým klientům.  
  
 Po absolvování řady témat v tomto kurzu budete mít funkční službu a klienta, který volá službu. První tři témata popisují postup definování kontraktu služby, jak implementovat kontrakt služby a k hostování služby. Vytvořená služba se hostuje sama v konzolové aplikaci. Služby může být také hostovaný v rámci Internetové informační služby (IIS). [!INCLUDE[crabout](../../../includes/crabout-md.md)] jak to udělat, najdete v části [postupy: hostování služby WCF ve službě IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md). Služba je nakonfigurována v kódu; služby však lze také nastavit v konfiguračním souboru. [!INCLUDE[crabout](../../../includes/crabout-md.md)] použití konfiguračního souboru najdete v části [konfigurace služeb pomocí konfiguračních souborů](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).  
  
 Následující tři témata popisují, jak vytvořit proxy klienta, nakonfigurovat klientskou aplikaci a používat proxy server klienta volat operace služby, které jsou vystavené službu. Služby publikování metadat, které definují informace, které klientské aplikace potřebuje ke komunikaci se službou. [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] automatizuje proces přístup k tato metadata a použije ho k vytvořit a nakonfigurovat klientskou aplikaci pro službu. Pokud nepoužíváte [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], můžete použít [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vytvořit a nakonfigurovat klientskou aplikaci pro službu.  
  
 Všechna témata v této části předpokládají, že jako vývojové prostředí používáte Visual Studio 2011. Pokud používáte jiné vývojové prostředí, ignorujte konkrétní pokyny Visual Studio.  
  
> [!NOTE]
>  Pokud používáte [!INCLUDE[wv](../../../includes/wv-md.md)] nebo novější verze operačního systému Windows, musíte spustit Visual Studio přejděte do nabídky Start a kliknutím pravým tlačítkem na Visual Studio 2011 a výběrem **spustit jako správce**. Vždy Visual Studio 2011 spustíte jako správce můžete vytvořit krátké vyjmutí, klikněte pravým tlačítkem na krátké vyjmutí, vyberte vlastnosti, vyberte **kompatibility** a zkontrolujte **spuštění tohoto programu jako správce** zaškrtávací políčko. Při spuštění sady Visual Studio 2011 s touto klávesovou, bude vždy spustit jako správce.  
  
 Ukázkové aplikace, které lze stáhnout na pevný disk a spusťte, najdete v tématech v [ukázky Windows Communication Foundation](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91). Pro toto téma, najdete v tématu, zejména [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
 Další podrobné informace o vytváření služeb a klientů najdete v tématu [základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 Popisuje postup vytvoření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sbalit pomocí uživatelské rozhraní. Kontrakt definuje funkce vystavené službou.  
  
 [Postupy: Implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 Popisuje způsob implementace kontraktu služby. Jakmile kontraktu definovat, musí být implementované pomocí třídy služby.  
  
 [Postupy: Hostování a spuštění základní služby](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 Popisuje postup konfigurace koncového bodu služby v kódu a k hostování služby v konzolové aplikaci. Stane aktivní, musí být služba nakonfigurována a hostovaným v rámci běhové prostředí. Toto prostředí vytvoří službu a ovládací prvky jeho kontextu a doba platnosti.  
  
 [Postupy: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 Popisuje, jak načíst metadata použít k vytvoření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] proxy serveru klienta z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Tento proces používá funkci Přidat odkaz na službu v rámci sady Visual Studio 2011.  
  
 [Postupy: Konfigurace klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 Popisuje postup konfigurace službou WCF klienta Konfigurace klienta vyžaduje zadání koncového bodu, který klient používá k přístupu ke službě.  
  
 [Postupy: Používání klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 Popisuje postup použití [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] proxy server klienta k vyvolání operace služby.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## <a name="related-sections"></a>Související oddíly  
 [Ukázky Windows Communication Foundation](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [Základní programovací životní cyklus](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepční přehled](../../../docs/framework/wcf/conceptual-overview.md)  
 [Průvodce dokumentací](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Co je Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Podrobnosti o funkcích WCF](../../../docs/framework/wcf/feature-details/index.md)
