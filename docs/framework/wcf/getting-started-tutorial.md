---
title: 'Kurz: Začínáme s aplikacemi Windows Communication Foundation'
description: Tyto kurzy poskytuje úvod pro vytváření wcf aplikací.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184112"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Kurz: Začínáme s aplikacemi Windows Communication Foundation
Následující série výukových programů vás seznámí s programovacím prostředím Windows Communication Foundation (WCF). Práce prostřednictvím těchto kurzů v pořadí vám poskytne úvodní pochopení kroků potřebných k vytvoření wcf aplikací. Po dokončení budete mít spuštěnou službu WCF a klienta WCF, který službu volá.

Kurz předpokládá, že používáte Visual Studio jako vývojové prostředí. Pokud používáte jiné vývojové prostředí, ignorujte pokyny specifické pro Visual Studio.

Ukázkové aplikace WCF, které můžete stáhnout a spustit, naleznete v [tématu Ukázky windows communication foundation](samples/index.md). Úvod do vzorků najdete v tématu [Ukázka Začínáme](samples/getting-started-sample.md).

Podrobnější informace o vytváření služeb a klientů naleznete v [tématu Basic WCF programming](basic-wcf-programming.md).

## <a name="wcf-tutorials"></a>Kurzy WCF

První tři kurzy popisují, jak definovat servisní smlouvu WCF, jak ji implementovat a jak ji hostovat. Služba, kterou vytvoříte, je hostována sama v rámci konzolové aplikace. Služby můžete hostovat také v rámci služby Microsoft Internet Information Services (IIS). Další informace naleznete v [tématu How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md). Přestože službu v kurzu nakonfigurujete pomocí kódu, můžete také [konfigurovat služby v konfiguračním souboru](configuring-services-using-configuration-files.md).

- [Kurz: Definování smlouvy o poskytování služeb](how-to-define-a-wcf-service-contract.md)

    Vytvoříte smlouvu WCF s uživatelem definovaným rozhraním. Tato smlouva definuje funkce, které služba zveřejňuje.

- [Kurz: Implementace smlouvy o poskytování služeb](how-to-implement-a-wcf-contract.md)

    Po definování smlouvy je nutné ji implementovat s třídou služeb.

- [Kurz: Hostování a spuštění základní služby](how-to-host-and-run-a-basic-wcf-service.md)

    Nakonfigurujte koncový bod pro službu a hostujte službu v aplikaci konzoly. Aby se služba stala aktivní, musíte ji nakonfigurovat a hostovat v prostředí za běhu. Toto prostředí run-time vytvoří službu a řídí její kontext a životnost.

Další dva kurzy popisují, jak vytvořit, nakonfigurovat a použít klientskou aplikaci k volání operací, které služba zveřejňuje. Služby publikují metadata, která definují informace, které klientská aplikace potřebuje ke komunikaci se službou. Visual Studio automatizuje proces přístupu k těmto metadatům a používá jej k vytvoření klientské aplikace pro službu. Pokud se rozhodnete nepoužívat Visual Studio, můžete místo toho použít [nástroj ServiceModel Metadata Utility (*Svcutil.exe*](servicemodel-metadata-utility-tool-svcutil-exe.md) ).

- [Kurz: Vytvoření klienta](how-to-create-a-wcf-client.md)

    Načtěte metadata pro vytvoření proxy klienta WCF ze služby WCF. Metadata načtete pomocí sady Visual Studio k přidání odkazu na službu nebo můžete použít nástroj ServiceModel Metadata Utility. Zadáte koncový bod, který klient používá pro přístup ke službě.

- [Kurz: Použití klienta](how-to-use-a-wcf-client.md)

    K volání operací služby použijte proxy klienta WCF.

## <a name="reference"></a>Referenční informace

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Viz také

- [Koncepční přehled](conceptual-overview.md)
- [Průvodce dokumentací](guide-to-the-documentation.md)
- [Co je Windows Communication Foundation](whats-wcf.md)
- [Podrobnosti o funkcích WCF](feature-details/index.md)
- [Základní životní cyklus programování](basic-programming-lifecycle.md)
- [Budování klientů](building-clients.md)
- [Základní programování WCF](basic-wcf-programming.md)
- [Postup: Vytvoření duplexní smlouvy](feature-details/how-to-create-a-duplex-contract.md)
- [Postup: Přístup ke službám s duplexní smlouvou](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Postup: Stažení dokumentů metadat pomocí nástroje Svcutil.exe](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Postup: Publikování metadat pro službu pomocí konfiguračního souboru](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Použití vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
- [Ukázka začínáme](samples/getting-started-sample.md)
- [Ukázky nadace Windows Communication Foundation](samples/index.md)
- [Vlastní hostování](samples/self-host.md)
