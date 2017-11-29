---
title: "Rozšíření systému metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cab59f5ddebdcc1e50921d5540d411e32b562341
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="5a06a-102">Rozšíření systému metadat</span><span class="sxs-lookup"><span data-stu-id="5a06a-102">Extending the Metadata System</span></span>
<span data-ttu-id="5a06a-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Systém metadat je skupina třídy a rozhraní, které představují metadata potřebnou k implementaci aplikace založené na služby.</span><span class="sxs-lookup"><span data-stu-id="5a06a-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="5a06a-104">Upravit nebo rozšíření třídy nebo implementovat a nakonfigurovat rozhraní pro export a import vlastních metadat, jako je například rozšíření webové služby popis Language (WSDL) nebo vlastní WS-PolicyAttachments kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="5a06a-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a06a-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5a06a-105">In This Section</span></span>  
 [<span data-ttu-id="5a06a-106">Export vlastních metadat pro rozšíření WCF</span><span class="sxs-lookup"><span data-stu-id="5a06a-106">Exporting Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="5a06a-107">Popisuje, jak implementovat a použít <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní pro vložení kontrolních výrazů vlastních zásad v dokumentech WSDL.</span><span class="sxs-lookup"><span data-stu-id="5a06a-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="5a06a-108">Import vlastních metadat pro rozšíření WCF</span><span class="sxs-lookup"><span data-stu-id="5a06a-108">Importing Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="5a06a-109">Popisuje, jak implementovat a použít <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> rozhraní ke čtení a reagovat na kontrolních výrazů vlastních zásad v dokumentech WSDL.</span><span class="sxs-lookup"><span data-stu-id="5a06a-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="5a06a-110">Publikování a načítání metadat prostřednictvím vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="5a06a-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="5a06a-111">Popisuje, jak k výměně metadat prostřednictvím vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="5a06a-111">Describes how to exchange metadata over custom bindings.</span></span>
