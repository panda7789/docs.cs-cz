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
# <a name="extending-the-metadata-system"></a><span data-ttu-id="234cb-102">Rozšíření systému metadat</span><span class="sxs-lookup"><span data-stu-id="234cb-102">Extending the Metadata System</span></span>
<span data-ttu-id="234cb-103">Systém metadat Windows Communication Foundation (WCF) je skupina tříd a rozhraní, která reprezentují metadata potřebná k implementaci aplikací založených na službách.</span><span class="sxs-lookup"><span data-stu-id="234cb-103">The Windows Communication Foundation (WCF) metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="234cb-104">Upravte nebo rozšíříte třídy nebo implementujte a konfigurujte rozhraní pro export a import vlastních metadat, jako jsou rozšíření jazyka WSDL (Web Services Description Language) nebo vlastní kontrolní výrazy WS-PolicyAttachments.</span><span class="sxs-lookup"><span data-stu-id="234cb-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="234cb-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="234cb-105">In This Section</span></span>  
 [<span data-ttu-id="234cb-106">Export vlastních metadat pro rozšíření WCF</span><span class="sxs-lookup"><span data-stu-id="234cb-106">Exporting Custom Metadata for a WCF Extension</span></span>](exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="234cb-107">Popisuje, jak implementovat a použít <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní pro vložení vlastních kontrolních výrazů zásad do dokumentů WSDL.</span><span class="sxs-lookup"><span data-stu-id="234cb-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="234cb-108">Import vlastních metadat pro rozšíření WCF</span><span class="sxs-lookup"><span data-stu-id="234cb-108">Importing Custom Metadata for a WCF Extension</span></span>](importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="234cb-109">Popisuje, jak implementovat a používat <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní ke čtení a reakci na vlastní kontrolní výrazy zásad v dokumentech WSDL.</span><span class="sxs-lookup"><span data-stu-id="234cb-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="234cb-110">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="234cb-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="234cb-111">Popisuje způsob, jak vyměňovat metadata přes vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="234cb-111">Describes how to exchange metadata over custom bindings.</span></span>
