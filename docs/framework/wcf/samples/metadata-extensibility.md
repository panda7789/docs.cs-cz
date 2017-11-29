---
title: "Rozšiřitelnost metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36eb5940fa1d869948a94fcbbb1945aea1c534ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-extensibility"></a>Rozšiřitelnost metadat
Tato část obsahuje příklady vysvětlující vlastních metadat.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vlastní zabezpečený koncový bod metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 Ukazuje, jak implementovat služby Zabezpečené metadata koncový bod, který používá jedna z vazeb neobsahující metadata exchange a postup konfigurace [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nebo klienty se načíst metadata z Tato metadata koncový bod.  
  
 [Vlastní publikování WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 Ukazuje, jak implementovat <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> na vlastní <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atribut, který chcete exportovat vlastnosti atribut jako WSDL poznámky mezi další funkce.
