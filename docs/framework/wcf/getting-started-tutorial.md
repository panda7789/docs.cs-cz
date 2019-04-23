---
title: 'Kurz: Začínáme s aplikacemi Windows Communication Foundation'
description: Tyto kurzy obsahuje úvod k vytváření aplikací WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: d4613edefeb8db2c0d1e11e925f8ac41329efb0d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137920"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Kurz: Začínáme s aplikacemi Windows Communication Foundation
Následující sérii kurzů vám představí pro Windows Communication Foundation (WCF) programovací prostředí. Práce prostřednictvím těchto kurzů v pořadí vám poskytne úvodní znalost kroky potřebné k vytváření aplikací WCF. Po dokončení budete mít spuštěnou službu WCF a klienta WCF, která volá službu. 

Kurz předpokládá, že používáte jako vývojové prostředí sady Visual Studio. Pokud používáte jiné vývojové prostředí, ignorujte Visual Studio konkrétní pokyny. 

Ukázkové aplikace WCF, které si můžete stáhnout a použít, najdete v části [ukázky Windows Communication Foundation](samples/index.md). Úvod k ukázkám, najdete v článku [ukázka Začínáme](samples/getting-started-sample.md).

Další podrobné informace o vytváření služeb a klientů najdete v tématu [základní programování WCF](basic-wcf-programming.md).

## <a name="wcf-tutorials"></a>Kurzy WCF

První tři kurzy popisují definování kontraktu služby WCF, implementaci a hostujte si ji. Je služba, kterou vytvoříte v rámci konzolové aplikace v místním prostředí. Můžete také hostování služeb v rámci Internetové informační služby (IIS). Další informace najdete v tématu [jak: Hostování služby WCF v IIS](feature-details/how-to-host-a-wcf-service-in-iis.md). I když ke konfiguraci služby v tomto kurzu použijete kódu, můžete také [konfigurace služby v konfiguračním souboru](configuring-services-using-configuration-files.md). 

- [Kurz: Definování kontraktu služby](how-to-define-a-wcf-service-contract.md)

    Vytvoření kontraktu WCF pomocí uživatelského rozhraní. Tento kontrakt definuje funkci, která poskytuje služby.

- [Kurz: Implementace kontraktu služby](how-to-implement-a-wcf-contract.md)

    Po definování kontraktu, je nutné implementovat s třídou služby.

- [Kurz: Hostování a spuštění základní služby](how-to-host-and-run-a-basic-wcf-service.md)

    Konfigurace koncového bodu služby a hostovat službu v konzolové aplikaci. Služba aktivuje musíte ji nakonfigurovat a hostování v rámci prostředí za běhu. Toto prostředí za běhu vytvoří službu a ovládací prvky jeho kontextu a životnosti.

Z následujících dvou kurzů popisuje, jak vytvořit, nakonfigurovat, a zpřístupňuje použití klientské aplikace k volání operací služby. Služby publikování metadat, které definují informace, které klientská aplikace potřebuje ke komunikaci se službou. Visual Studio automatizuje proces přístup k tato metadata a použije je k vytvoření klientské aplikace pro službu. Pokud se rozhodnete nepoužívat sady Visual Studio, můžete použít [nástroj ServiceModel Metadata Utility (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) místo.

- [Kurz: Vytvoření klienta](how-to-create-a-wcf-client.md)

    Načtěte metadata k vytvoření proxy serveru klienta WCF na službu WCF. Načítání metadat pomocí sady Visual Studio pro přidání odkazu na službu nebo můžete použít nástroj ServiceModel Metadata Utility. Zadáte koncový bod, který klient používá pro přístup ke službě.

- [Kurz: Používání klienta](how-to-use-a-wcf-client.md)

    Použijte proxy klienta WCF k volání operací služby.

## <a name="reference"></a>Odkaz

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Viz také:

- [Koncepční přehled](conceptual-overview.md)
- [Příručka k dokumentaci](guide-to-the-documentation.md)
- [Co je Windows Communication Foundation](whats-wcf.md)
- [Podrobnosti o funkcích WCF](feature-details/index.md)
- [Základní programovací životní cyklus](basic-programming-lifecycle.md)
- [Sestavování klientů](building-clients.md)
- [Základní programování WCF](basic-wcf-programming.md)
- [Postupy: Vytvoření duplexního kontraktu](feature-details/how-to-create-a-duplex-contract.md)
- [Postupy: Přístup ke službám pomocí duplexního kontraktu](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Postupy: Stažení dokumentů metadat pomocí Svcutil.exe](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Postupy: Publikování metadat služby promocí konfiguračního souboru](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
- [Ukázka Začínáme](samples/getting-started-sample.md)
- [Ukázky Windows Communication Foundation](samples/index.md)
- [Vlastní hostování](samples/self-host.md)
