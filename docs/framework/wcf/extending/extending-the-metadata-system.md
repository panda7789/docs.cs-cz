---
title: Rozšíření systému metadat
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: d3ce7e1a228e6303be1009c7b72f4e889b40c536
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795717"
---
# <a name="extending-the-metadata-system"></a>Rozšíření systému metadat
Systém metadat Windows Communication Foundation (WCF) je skupina tříd a rozhraní, která reprezentují metadata potřebná k implementaci aplikací založených na službách. Upravte nebo rozšíříte třídy nebo implementujte a konfigurujte rozhraní pro export a import vlastních metadat, jako jsou rozšíření jazyka WSDL (Web Services Description Language) nebo vlastní kontrolní výrazy WS-PolicyAttachments.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Export vlastních metadat pro rozšíření WCF](exporting-custom-metadata-for-a-wcf-extension.md)  
 Popisuje, jak implementovat a použít <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní pro vložení vlastních kontrolních výrazů zásad do dokumentů WSDL.  
  
 [Import vlastních metadat pro rozšíření WCF](importing-custom-metadata-for-a-wcf-extension.md)  
 Popisuje, jak implementovat a používat <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní ke čtení a reakci na vlastní kontrolní výrazy zásad v dokumentech WSDL.  
  
 [Publikování a načítání metadat prostřednictvím vlastní vazby](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 Popisuje způsob, jak vyměňovat metadata přes vlastní vazby.
