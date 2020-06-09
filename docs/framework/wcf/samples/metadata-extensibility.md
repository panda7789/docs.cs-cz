---
title: Rozšiřitelnost metadat
ms.date: 03/30/2017
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
ms.openlocfilehash: 1e8e7f511b38cf3326b9abbca57df769317a26a4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584620"
---
# <a name="metadata-extensibility"></a>Rozšiřitelnost metadat
Tato část obsahuje ukázky, které ukazují vlastní metadata.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vlastní zabezpečený koncový bod metadat](custom-secure-metadata-endpoint.md)  
 Ukazuje, jak implementovat službu pomocí zabezpečeného koncového bodu metadat, který používá jednu z vazeb, které neobsahují metadata, a jak nakonfigurovat nástroj pro nástroj pro dokládání metadat [(Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) nebo klienty, aby načetl metadata z takového koncového bodu metadat.  
  
 [Vlastní publikování WSDL](custom-wsdl-publication.md)  
 Ukazuje, jak implementovat a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> u vlastního <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atributu pro export vlastností atributu jako anotace WSDL, mimo jiné funkce.
