---
title: ClientCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 68a2fa36c8a4fa1fde3ca8d8aaf1898060ea972f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="clientcredentials"></a><span data-ttu-id="0f694-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="0f694-102">ClientCredentials</span></span>
<span data-ttu-id="0f694-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="0f694-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f694-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f694-104">Syntax</span></span>  
  
```  
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0f694-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0f694-105">Methods</span></span>  
 <span data-ttu-id="0f694-106">Třída ClientCredentials nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="0f694-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0f694-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0f694-107">Properties</span></span>  
 <span data-ttu-id="0f694-108">Třída ClientCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="0f694-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="0f694-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="0f694-109">ClientCertificate</span></span>  
 <span data-ttu-id="0f694-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0f694-110">Data type: string</span></span>  
  
 <span data-ttu-id="0f694-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0f694-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f694-112">Certifikát X.509 klienta používá k ověření služby.</span><span class="sxs-lookup"><span data-stu-id="0f694-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="0f694-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="0f694-113">HttpDigest</span></span>  
 <span data-ttu-id="0f694-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0f694-114">Data type: string</span></span>  
  
 <span data-ttu-id="0f694-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0f694-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f694-116">Aktuální pověření Http Digest.</span><span class="sxs-lookup"><span data-stu-id="0f694-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="0f694-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="0f694-117">IssuedToken</span></span>  
 <span data-ttu-id="0f694-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0f694-118">Data type: string</span></span>  
  
 <span data-ttu-id="0f694-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0f694-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f694-120">Adresa koncového bodu a vazba použitá ke kontaktování služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0f694-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="0f694-121">sdílené</span><span class="sxs-lookup"><span data-stu-id="0f694-121">Peer</span></span>  
 <span data-ttu-id="0f694-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0f694-122">Data type: string</span></span>  
  
 <span data-ttu-id="0f694-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0f694-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f694-124">Pověření, které používá uzlu druhé strany ke svému ověření do dalších uzlů v mřížce.</span><span class="sxs-lookup"><span data-stu-id="0f694-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="0f694-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="0f694-125">ServiceCertificate</span></span>  
 <span data-ttu-id="0f694-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0f694-126">Data type: string</span></span>  
  
 <span data-ttu-id="0f694-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0f694-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f694-128">Certifikát X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="0f694-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="0f694-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="0f694-129">SupportInteractive</span></span>  
 <span data-ttu-id="0f694-130">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="0f694-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="0f694-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0f694-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f694-132">Logická hodnota, která určuje, zda pověření podporuje interaktivní vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="0f694-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="0f694-133">UserName</span><span class="sxs-lookup"><span data-stu-id="0f694-133">UserName</span></span>  
 <span data-ttu-id="0f694-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0f694-134">Data type: string</span></span>  
  
 <span data-ttu-id="0f694-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0f694-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f694-136">Uživatelské jméno a heslo, které klient používá k ověření samotné služby.</span><span class="sxs-lookup"><span data-stu-id="0f694-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="0f694-137">Windows</span><span class="sxs-lookup"><span data-stu-id="0f694-137">Windows</span></span>  
 <span data-ttu-id="0f694-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0f694-138">Data type: string</span></span>  
  
 <span data-ttu-id="0f694-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0f694-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f694-140">Přihlašovací údaje windows používá klienta ke svému ověření ke službě.</span><span class="sxs-lookup"><span data-stu-id="0f694-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f694-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f694-141">Requirements</span></span>  
  
|<span data-ttu-id="0f694-142">MOF</span><span class="sxs-lookup"><span data-stu-id="0f694-142">MOF</span></span>|<span data-ttu-id="0f694-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0f694-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0f694-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="0f694-144">Namespace</span></span>|<span data-ttu-id="0f694-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0f694-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f694-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f694-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
