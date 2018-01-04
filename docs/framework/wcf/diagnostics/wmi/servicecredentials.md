---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73fad36b5bf14745ca70d297fa988b90d46990df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="30931-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="30931-102">ServiceCredentials</span></span>
<span data-ttu-id="30931-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="30931-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30931-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30931-104">Syntax</span></span>  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="30931-105">Metody</span><span class="sxs-lookup"><span data-stu-id="30931-105">Methods</span></span>  
 <span data-ttu-id="30931-106">Třída – ServiceCredentials nejsou definovány žádné metody.</span><span class="sxs-lookup"><span data-stu-id="30931-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="30931-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="30931-107">Properties</span></span>  
 <span data-ttu-id="30931-108">Třída – ServiceCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="30931-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="30931-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="30931-109">ClientCertificate</span></span>  
 <span data-ttu-id="30931-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30931-110">Data type: string</span></span>  
  
 <span data-ttu-id="30931-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30931-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30931-112">Certifikát ověřování a zřizování nastavení klienta pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="30931-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="30931-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="30931-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="30931-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30931-114">Data type: string</span></span>  
  
 <span data-ttu-id="30931-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30931-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30931-116">Aktuální vydaný nastavení ověření pomocí tokenu pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="30931-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="30931-117">sdílené</span><span class="sxs-lookup"><span data-stu-id="30931-117">Peer</span></span>  
 <span data-ttu-id="30931-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30931-118">Data type: string</span></span>  
  
 <span data-ttu-id="30931-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30931-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30931-120">Aktuální přihlašovací údaje, ověřování a nastavení, která má být používána koncových bodů přenosu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="30931-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="30931-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="30931-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="30931-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30931-122">Data type: string</span></span>  
  
 <span data-ttu-id="30931-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30931-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30931-124">Určuje aktuální nastavení zabezpečené konverzaci.</span><span class="sxs-lookup"><span data-stu-id="30931-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="30931-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="30931-125">ServiceCertificate</span></span>  
 <span data-ttu-id="30931-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30931-126">Data type: string</span></span>  
  
 <span data-ttu-id="30931-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30931-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30931-128">Certifikát přidružený k této službě.</span><span class="sxs-lookup"><span data-stu-id="30931-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="30931-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="30931-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="30931-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30931-130">Data type: string</span></span>  
  
 <span data-ttu-id="30931-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30931-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30931-132">Nastavení uživatelského jména a hesla pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="30931-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="30931-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="30931-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="30931-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30931-134">Data type: string</span></span>  
  
 <span data-ttu-id="30931-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30931-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30931-136">Nastavení ověřování systému Windows pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="30931-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30931-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30931-137">Requirements</span></span>  
  
|<span data-ttu-id="30931-138">MOF</span><span class="sxs-lookup"><span data-stu-id="30931-138">MOF</span></span>|<span data-ttu-id="30931-139">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="30931-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="30931-140">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="30931-140">Namespace</span></span>|<span data-ttu-id="30931-141">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="30931-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30931-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="30931-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
