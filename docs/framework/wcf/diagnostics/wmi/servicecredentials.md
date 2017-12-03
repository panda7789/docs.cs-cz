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
ms.openlocfilehash: 89aff21ed916e1b486a191f86dde5ed8b3e4ba22
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="88b8e-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="88b8e-102">ServiceCredentials</span></span>
<span data-ttu-id="88b8e-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="88b8e-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88b8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88b8e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="88b8e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="88b8e-105">Methods</span></span>  
 <span data-ttu-id="88b8e-106">Třída – ServiceCredentials nejsou definovány žádné metody.</span><span class="sxs-lookup"><span data-stu-id="88b8e-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="88b8e-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="88b8e-107">Properties</span></span>  
 <span data-ttu-id="88b8e-108">Třída – ServiceCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="88b8e-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="88b8e-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="88b8e-109">ClientCertificate</span></span>  
 <span data-ttu-id="88b8e-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="88b8e-110">Data type: string</span></span>  
  
 <span data-ttu-id="88b8e-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="88b8e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88b8e-112">Certifikát ověřování a zřizování nastavení klienta pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="88b8e-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="88b8e-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="88b8e-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="88b8e-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="88b8e-114">Data type: string</span></span>  
  
 <span data-ttu-id="88b8e-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="88b8e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88b8e-116">Aktuální vydaný nastavení ověření pomocí tokenu pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="88b8e-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="88b8e-117">sdílené</span><span class="sxs-lookup"><span data-stu-id="88b8e-117">Peer</span></span>  
 <span data-ttu-id="88b8e-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="88b8e-118">Data type: string</span></span>  
  
 <span data-ttu-id="88b8e-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="88b8e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88b8e-120">Aktuální přihlašovací údaje, ověřování a nastavení, která má být používána koncových bodů přenosu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="88b8e-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="88b8e-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="88b8e-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="88b8e-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="88b8e-122">Data type: string</span></span>  
  
 <span data-ttu-id="88b8e-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="88b8e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88b8e-124">Určuje aktuální nastavení zabezpečené konverzaci.</span><span class="sxs-lookup"><span data-stu-id="88b8e-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="88b8e-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="88b8e-125">ServiceCertificate</span></span>  
 <span data-ttu-id="88b8e-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="88b8e-126">Data type: string</span></span>  
  
 <span data-ttu-id="88b8e-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="88b8e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88b8e-128">Certifikát přidružený k této službě.</span><span class="sxs-lookup"><span data-stu-id="88b8e-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="88b8e-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="88b8e-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="88b8e-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="88b8e-130">Data type: string</span></span>  
  
 <span data-ttu-id="88b8e-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="88b8e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88b8e-132">Nastavení uživatelského jména a hesla pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="88b8e-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="88b8e-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="88b8e-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="88b8e-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="88b8e-134">Data type: string</span></span>  
  
 <span data-ttu-id="88b8e-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="88b8e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88b8e-136">Nastavení ověřování systému Windows pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="88b8e-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88b8e-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88b8e-137">Requirements</span></span>  
  
|<span data-ttu-id="88b8e-138">MOF</span><span class="sxs-lookup"><span data-stu-id="88b8e-138">MOF</span></span>|<span data-ttu-id="88b8e-139">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="88b8e-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="88b8e-140">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="88b8e-140">Namespace</span></span>|<span data-ttu-id="88b8e-141">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="88b8e-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88b8e-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="88b8e-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
