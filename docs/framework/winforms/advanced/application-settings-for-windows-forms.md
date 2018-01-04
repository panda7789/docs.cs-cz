---
title: "Nastavení aplikace pro Windows Forms"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ClientApplicationSettings
helpviewer_keywords:
- application settings [Windows Forms]
- Windows Forms, application settings
ms.assetid: 64090a34-8556-4904-8ea0-20efe9f8c886
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63248009497152a41a6313a50ed6e7544ac62cbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="application-settings-for-windows-forms"></a><span data-ttu-id="cf65a-102">Nastavení aplikace pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf65a-102">Application Settings for Windows Forms</span></span>
<span data-ttu-id="cf65a-103">Funkce nastavení aplikace Windows Forms umožňuje snadno vytvářet, ukládat a udržovat vlastní aplikaci a uživatelské předvolby v klientovi.</span><span class="sxs-lookup"><span data-stu-id="cf65a-103">The Applications Settings feature of Windows Forms makes it easy to create, store, and maintain custom application and user preferences on the client.</span></span> <span data-ttu-id="cf65a-104">Pomocí nastavení aplikace můžete uložit pouze data aplikací, jako je například databázové připojovací řetězce, ale také uživatelská data, jako třeba pozic panelu nástrojů a naposledy použít seznamy.</span><span class="sxs-lookup"><span data-stu-id="cf65a-104">With Application Settings, you can store not only application data such as database connection strings, but also user-specific data, such as toolbar positions and most-recently used lists.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf65a-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cf65a-105">In This Section</span></span>  
 [<span data-ttu-id="cf65a-106">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="cf65a-106">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)  
 <span data-ttu-id="cf65a-107">Popisuje postup vytvoření a uložení dat nastavení jménem vaší aplikace a uživatele.</span><span class="sxs-lookup"><span data-stu-id="cf65a-107">Discusses how to create and store settings data on behalf of your application and your users.</span></span>  
  
 [<span data-ttu-id="cf65a-108">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="cf65a-108">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)  
 <span data-ttu-id="cf65a-109">Popisuje, jak funkce funguje v nastavení aplikace a jsou zde popsány pokročilé funkce architektury, jako jsou seskupené nastavení a nastavení klíče.</span><span class="sxs-lookup"><span data-stu-id="cf65a-109">Describes how the Application Settings feature works, and explores advanced features of the architecture such as grouped settings and settings keys.</span></span>  
  
 [<span data-ttu-id="cf65a-110">Atributy nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="cf65a-110">Application Settings Attributes</span></span>](~/docs/framework/winforms/advanced/application-settings-attributes.md)  
 <span data-ttu-id="cf65a-111">Uvádí a popisuje atributy, které můžete použít pro třídu obálky nastavení aplikace nebo jeho nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cf65a-111">Lists and describes the attributes that can be applied to an application settings wrapper class or its settings properties.</span></span>  
  
 [<span data-ttu-id="cf65a-112">Nastavení aplikace pro vlastní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="cf65a-112">Application Settings for Custom Controls</span></span>](~/docs/framework/winforms/advanced/application-settings-for-custom-controls.md)  
 <span data-ttu-id="cf65a-113">Popisuje, co je třeba provést poskytnout vlastní ovládací prvky umožňuje zachovat nastavení aplikace, když jsou hostované v aplikacích třetích stran.</span><span class="sxs-lookup"><span data-stu-id="cf65a-113">Discusses what must be done to give your custom controls the ability to persist application settings when hosted in third-party applications.</span></span>  
  
 [<span data-ttu-id="cf65a-114">Postupy: Vytváření nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="cf65a-114">How to: Create Application Settings</span></span>](~/docs/framework/winforms/advanced/how-to-create-application-settings.md)  
 <span data-ttu-id="cf65a-115">Ukazuje vytvoření nové nastavení aplikace, které jsou nastavené jako trvalé mezi relacemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf65a-115">Demonstrates creating new application settings that are persisted between application sessions.</span></span>  
  
 [<span data-ttu-id="cf65a-116">Postupy: Ověření nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="cf65a-116">How to: Validate Application Settings</span></span>](~/docs/framework/winforms/advanced/how-to-validate-application-settings.md)  
 <span data-ttu-id="cf65a-117">Ukazuje nastavení ověřování aplikace předtím, než jsou nastavené jako trvalé.</span><span class="sxs-lookup"><span data-stu-id="cf65a-117">Demonstrates validating application settings before they are persisted.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="cf65a-118">Související témata</span><span class="sxs-lookup"><span data-stu-id="cf65a-118">Related topics</span></span>

<span data-ttu-id="cf65a-119">[Windows Forms konfigurační oddíl](../../../../docs/framework/configure-apps/file-schema/winforms/index.md)  </span><span class="sxs-lookup"><span data-stu-id="cf65a-119">[Windows Forms Configuration Section](../../../../docs/framework/configure-apps/file-schema/winforms/index.md)  </span></span>  
<span data-ttu-id="cf65a-120">Dokumenty nastavení pro povolení vysoké DPI podporují ve formulářové aplikaci Windows od verze 4.7 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf65a-120">Documents the settings to enable High DPI support in Windows Forms Application starting with the .NET Framework 4.7.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf65a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf65a-121">See also</span></span>  
  
[<span data-ttu-id="cf65a-122">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf65a-122">Windows Forms</span></span>](../index.md)
