---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: bf906e09ae71d26f8e95877f1c545c0724d57b9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485735"
---
# <a name="servicecredentials"></a><span data-ttu-id="72f27-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="72f27-102">ServiceCredentials</span></span>
<span data-ttu-id="72f27-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="72f27-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72f27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72f27-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="72f27-105">Metody</span><span class="sxs-lookup"><span data-stu-id="72f27-105">Methods</span></span>  
 <span data-ttu-id="72f27-106">Třída – ServiceCredentials nejsou definovány žádné metody.</span><span class="sxs-lookup"><span data-stu-id="72f27-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="72f27-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="72f27-107">Properties</span></span>  
 <span data-ttu-id="72f27-108">Třída – ServiceCredentials má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="72f27-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="72f27-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="72f27-109">ClientCertificate</span></span>  
 <span data-ttu-id="72f27-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="72f27-110">Data type: string</span></span>  
  
 <span data-ttu-id="72f27-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="72f27-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72f27-112">Certifikát ověřování a zřizování nastavení klienta pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="72f27-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="72f27-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="72f27-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="72f27-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="72f27-114">Data type: string</span></span>  
  
 <span data-ttu-id="72f27-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="72f27-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72f27-116">Aktuální vydaný nastavení ověření pomocí tokenu pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="72f27-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="72f27-117">sdílené</span><span class="sxs-lookup"><span data-stu-id="72f27-117">Peer</span></span>  
 <span data-ttu-id="72f27-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="72f27-118">Data type: string</span></span>  
  
 <span data-ttu-id="72f27-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="72f27-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72f27-120">Aktuální přihlašovací údaje, ověřování a nastavení, která má být používána koncových bodů přenosu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="72f27-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="72f27-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="72f27-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="72f27-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="72f27-122">Data type: string</span></span>  
  
 <span data-ttu-id="72f27-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="72f27-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72f27-124">Určuje aktuální nastavení zabezpečené konverzaci.</span><span class="sxs-lookup"><span data-stu-id="72f27-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="72f27-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="72f27-125">ServiceCertificate</span></span>  
 <span data-ttu-id="72f27-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="72f27-126">Data type: string</span></span>  
  
 <span data-ttu-id="72f27-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="72f27-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72f27-128">Certifikát přidružený k této službě.</span><span class="sxs-lookup"><span data-stu-id="72f27-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="72f27-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="72f27-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="72f27-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="72f27-130">Data type: string</span></span>  
  
 <span data-ttu-id="72f27-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="72f27-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72f27-132">Nastavení uživatelského jména a hesla pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="72f27-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="72f27-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="72f27-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="72f27-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="72f27-134">Data type: string</span></span>  
  
 <span data-ttu-id="72f27-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="72f27-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72f27-136">Nastavení ověřování systému Windows pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="72f27-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72f27-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72f27-137">Requirements</span></span>  
  
|<span data-ttu-id="72f27-138">MOF</span><span class="sxs-lookup"><span data-stu-id="72f27-138">MOF</span></span>|<span data-ttu-id="72f27-139">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="72f27-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="72f27-140">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="72f27-140">Namespace</span></span>|<span data-ttu-id="72f27-141">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="72f27-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72f27-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="72f27-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
