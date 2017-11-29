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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4cc9d7d7d46157b7df202c6daffb31b90fa98c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="329a6-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="329a6-102">ServiceCredentials</span></span>
<span data-ttu-id="329a6-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="329a6-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="329a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="329a6-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="329a6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="329a6-105">Methods</span></span>  
 <span data-ttu-id="329a6-106">Třída – ServiceCredentials nejsou definovány žádné metody.</span><span class="sxs-lookup"><span data-stu-id="329a6-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="329a6-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="329a6-107">Properties</span></span>  
 <span data-ttu-id="329a6-108">Třída – ServiceCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="329a6-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="329a6-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="329a6-109">ClientCertificate</span></span>  
 <span data-ttu-id="329a6-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="329a6-110">Data type: string</span></span>  
  
 <span data-ttu-id="329a6-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="329a6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="329a6-112">Certifikát ověřování a zřizování nastavení klienta pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="329a6-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="329a6-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="329a6-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="329a6-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="329a6-114">Data type: string</span></span>  
  
 <span data-ttu-id="329a6-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="329a6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="329a6-116">Aktuální vydaný nastavení ověření pomocí tokenu pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="329a6-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="329a6-117">sdílené</span><span class="sxs-lookup"><span data-stu-id="329a6-117">Peer</span></span>  
 <span data-ttu-id="329a6-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="329a6-118">Data type: string</span></span>  
  
 <span data-ttu-id="329a6-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="329a6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="329a6-120">Aktuální přihlašovací údaje, ověřování a nastavení, která má být používána koncových bodů přenosu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="329a6-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="329a6-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="329a6-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="329a6-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="329a6-122">Data type: string</span></span>  
  
 <span data-ttu-id="329a6-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="329a6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="329a6-124">Určuje aktuální nastavení zabezpečené konverzaci.</span><span class="sxs-lookup"><span data-stu-id="329a6-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="329a6-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="329a6-125">ServiceCertificate</span></span>  
 <span data-ttu-id="329a6-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="329a6-126">Data type: string</span></span>  
  
 <span data-ttu-id="329a6-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="329a6-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="329a6-128">Certifikát přidružený k této službě.</span><span class="sxs-lookup"><span data-stu-id="329a6-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="329a6-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="329a6-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="329a6-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="329a6-130">Data type: string</span></span>  
  
 <span data-ttu-id="329a6-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="329a6-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="329a6-132">Nastavení uživatelského jména a hesla pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="329a6-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="329a6-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="329a6-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="329a6-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="329a6-134">Data type: string</span></span>  
  
 <span data-ttu-id="329a6-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="329a6-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="329a6-136">Nastavení ověřování systému Windows pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="329a6-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="329a6-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="329a6-137">Requirements</span></span>  
  
|<span data-ttu-id="329a6-138">MOF</span><span class="sxs-lookup"><span data-stu-id="329a6-138">MOF</span></span>|<span data-ttu-id="329a6-139">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="329a6-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="329a6-140">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="329a6-140">Namespace</span></span>|<span data-ttu-id="329a6-141">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="329a6-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="329a6-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="329a6-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
