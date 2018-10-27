---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 26bd0c95f930bf7859ae6409d797afbb596844fa
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180663"
---
# <a name="servicecredentials"></a><span data-ttu-id="1d258-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="1d258-102">ServiceCredentials</span></span>
<span data-ttu-id="1d258-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="1d258-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d258-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d258-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="1d258-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1d258-105">Methods</span></span>  
 <span data-ttu-id="1d258-106">Třídu ServiceCredentials nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="1d258-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1d258-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1d258-107">Properties</span></span>  
 <span data-ttu-id="1d258-108">Třídu ServiceCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="1d258-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="1d258-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="1d258-109">ClientCertificate</span></span>  
 <span data-ttu-id="1d258-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1d258-110">Data type: string</span></span>  
  
 <span data-ttu-id="1d258-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1d258-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1d258-112">Certifikát ověření a opatření nastavení klienta pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="1d258-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="1d258-113">issuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="1d258-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="1d258-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1d258-114">Data type: string</span></span>  
  
 <span data-ttu-id="1d258-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1d258-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1d258-116">Aktuálně vydaného tokenu ověřování nastavení pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="1d258-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="1d258-117">Peer</span><span class="sxs-lookup"><span data-stu-id="1d258-117">Peer</span></span>  
 <span data-ttu-id="1d258-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1d258-118">Data type: string</span></span>  
  
 <span data-ttu-id="1d258-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1d258-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1d258-120">Aktuální pověření ověřování a zřizování nastavení používané koncových bodů přenosu stejné.</span><span class="sxs-lookup"><span data-stu-id="1d258-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="1d258-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="1d258-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="1d258-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1d258-122">Data type: string</span></span>  
  
 <span data-ttu-id="1d258-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1d258-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1d258-124">Určuje aktuální nastavení zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="1d258-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="1d258-125">serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="1d258-125">ServiceCertificate</span></span>  
 <span data-ttu-id="1d258-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1d258-126">Data type: string</span></span>  
  
 <span data-ttu-id="1d258-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1d258-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1d258-128">Platnost certifikátu spojeného s touto službou.</span><span class="sxs-lookup"><span data-stu-id="1d258-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="1d258-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="1d258-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="1d258-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1d258-130">Data type: string</span></span>  
  
 <span data-ttu-id="1d258-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1d258-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1d258-132">Nastavení uživatelského jména a hesla pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="1d258-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="1d258-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="1d258-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="1d258-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1d258-134">Data type: string</span></span>  
  
 <span data-ttu-id="1d258-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1d258-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1d258-136">Nastavení ověřování Windows pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="1d258-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d258-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d258-137">Requirements</span></span>  
  
|<span data-ttu-id="1d258-138">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="1d258-138">MOF</span></span>|<span data-ttu-id="1d258-139">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1d258-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1d258-140">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="1d258-140">Namespace</span></span>|<span data-ttu-id="1d258-141">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1d258-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d258-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d258-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
