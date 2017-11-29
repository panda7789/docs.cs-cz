---
title: "Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: afee838dac830d060ac933f314d3a57dcc11d603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="47e18-102">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="47e18-102">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>
<span data-ttu-id="47e18-103">Řízení přístupu k prostředkům v počítači domény systému Windows je úloha základní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="47e18-103">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="47e18-104">Například pouze určité uživatelé by měli být schopní zobrazit citlivá data, jako jsou informace o mzdách.</span><span class="sxs-lookup"><span data-stu-id="47e18-104">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="47e18-105">Toto téma vysvětluje, jak omezit přístup k metodě pomocí vyžadování, které uživatel patří do předdefinované skupiny.</span><span class="sxs-lookup"><span data-stu-id="47e18-105">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="47e18-106">Pracovní vzorek, najdete v části [autorizace přístupu k operacím služby](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="47e18-106">For a working sample, see [Authorizing Access to Service Operations](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="47e18-107">Úloha se skládá z dva samostatné postupy.</span><span class="sxs-lookup"><span data-stu-id="47e18-107">The task consists of two separate procedures.</span></span> <span data-ttu-id="47e18-108">První vytvoří skupinu a naplní s uživateli.</span><span class="sxs-lookup"><span data-stu-id="47e18-108">The first creates the group and populates it with users.</span></span> <span data-ttu-id="47e18-109">Druhá <xref:System.Security.Permissions.PrincipalPermissionAttribute> třídy zadejte skupinu.</span><span class="sxs-lookup"><span data-stu-id="47e18-109">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="47e18-110">Chcete-li vytvořit skupiny systému Windows</span><span class="sxs-lookup"><span data-stu-id="47e18-110">To create a Windows group</span></span>  
  
1.  <span data-ttu-id="47e18-111">Otevřete **Správa počítače** konzoly.</span><span class="sxs-lookup"><span data-stu-id="47e18-111">Open the **Computer Management** console.</span></span>  
  
2.  <span data-ttu-id="47e18-112">V levém panelu klikněte na **místní uživatelé a skupiny**.</span><span class="sxs-lookup"><span data-stu-id="47e18-112">In the left panel, click **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="47e18-113">Klikněte pravým tlačítkem na **skupiny**a klikněte na tlačítko **nová skupina**.</span><span class="sxs-lookup"><span data-stu-id="47e18-113">Right-click **Groups**, and click **New Group**.</span></span>  
  
4.  <span data-ttu-id="47e18-114">V **název skupiny** zadejte název nové skupiny.</span><span class="sxs-lookup"><span data-stu-id="47e18-114">In the **Group Name** box, type a name for the new group.</span></span>  
  
5.  <span data-ttu-id="47e18-115">V **popis** zadejte popis nové skupiny.</span><span class="sxs-lookup"><span data-stu-id="47e18-115">In the **Description** box, type a description of the new group.</span></span>  
  
6.  <span data-ttu-id="47e18-116">Klikněte **přidat** tlačítko Přidat nové členy do skupiny.</span><span class="sxs-lookup"><span data-stu-id="47e18-116">Click the **Add** button to add new members to the group.</span></span>  
  
7.  <span data-ttu-id="47e18-117">Pokud jste sami přidali do skupiny a chcete otestovat následující kód, je nutné odhlásit počítač a znovu přihlásit, aby se ve skupině obsaženy.</span><span class="sxs-lookup"><span data-stu-id="47e18-117">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="47e18-118">Vyžádání uživatele členství</span><span class="sxs-lookup"><span data-stu-id="47e18-118">To demand user membership</span></span>  
  
1.  <span data-ttu-id="47e18-119">Otevřete [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] soubor kódu, který obsahuje kód kontraktu implementovaná službu.</span><span class="sxs-lookup"><span data-stu-id="47e18-119">Open the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] code file that contains the implemented service contract code.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="47e18-120">implementace kontraktu, najdete v části [implementace kontraktů služby](../../../docs/framework/wcf/implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="47e18-120"> implementing a contract, see [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="47e18-121">Použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut každá metoda, která musí být omezeno na konkrétní skupinu.</span><span class="sxs-lookup"><span data-stu-id="47e18-121">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="47e18-122">Nastavte <xref:System.Security.Permissions.SecurityAttribute.Action%2A> vlastnost <xref:System.Security.Permissions.SecurityAction.Demand> a <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> vlastnost na název skupiny.</span><span class="sxs-lookup"><span data-stu-id="47e18-122">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="47e18-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="47e18-123">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="47e18-124">Pokud použijete <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut kontraktu <xref:System.Security.SecurityException> bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="47e18-124">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="47e18-125">Lze použít pouze atribut na úrovni metody.</span><span class="sxs-lookup"><span data-stu-id="47e18-125">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="47e18-126">Použití certifikátu pro řízení přístupu k metodě</span><span class="sxs-lookup"><span data-stu-id="47e18-126">Using a Certificate to Control Access to a Method</span></span>  
 <span data-ttu-id="47e18-127">Můžete také `PrincipalPermissionAttribute` třída k řízení přístupu k metodu, pokud je certifikát typu pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="47e18-127">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="47e18-128">Chcete-li to provést, musí mít předmětu a kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="47e18-128">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="47e18-129">Chcete-li prozkoumat certifikát pro jeho vlastnosti, přečtěte si téma [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="47e18-129">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="47e18-130">Hodnota kryptografického otisku, najdete v tématu [postupy: načtení kryptografického otisku certifikátu](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="47e18-130">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="47e18-131">Pokud chcete řídit přístup pomocí certifikátu</span><span class="sxs-lookup"><span data-stu-id="47e18-131">To control access using a certificate</span></span>  
  
1.  <span data-ttu-id="47e18-132">Použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> třída metodu, kterou chcete omezit přístup k.</span><span class="sxs-lookup"><span data-stu-id="47e18-132">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2.  <span data-ttu-id="47e18-133">Nastavení akce atributu <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47e18-133">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3.  <span data-ttu-id="47e18-134">Nastavte `Name` vlastnost na řetězec, který se skládá z název předmětu a kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="47e18-134">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="47e18-135">Oddělte dvě hodnoty středník a mezeru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="47e18-135">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  <span data-ttu-id="47e18-136">Nastavte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> jak je znázorněno v následujícím příkladu konfigurace:</span><span class="sxs-lookup"><span data-stu-id="47e18-136">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="47e18-137">Nastavení této hodnoty na `UseAspNetRoles` znamená, že `Name` vlastnost `PrincipalPermissionAttribute` se použije k provádění porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="47e18-137">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="47e18-138">Když je certifikát použit jako pověření klienta, ve výchozím nastavení [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zřetězí běžný název certifikátu a kryptografický otisk středníkem k vytvoření jedinečné hodnoty pro primární identitu klienta.</span><span class="sxs-lookup"><span data-stu-id="47e18-138">When a certificate is used as a client credential, by default [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="47e18-139">S `UseAspNetRoles` nastavit jako `PrincipalPermissionMode` na službu, tato hodnota primární identity se porovná s `Name` hodnotu vlastnosti k určení přístupová práva uživatele.</span><span class="sxs-lookup"><span data-stu-id="47e18-139">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="47e18-140">Můžete taky při vytváření samoobslužné hostovanou službu, nastavte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastností v kódu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="47e18-140">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="47e18-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="47e18-141">See Also</span></span>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.SecurityAction.Demand>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>  
 [<span data-ttu-id="47e18-142">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="47e18-142">Authorizing Access to Service Operations</span></span>](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="47e18-143">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="47e18-143">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="47e18-144">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="47e18-144">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
