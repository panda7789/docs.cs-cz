---
title: 'Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: ae2aa4c5629096ee7d888e7c4e334c3b6696db3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323314"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="be004-102">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="be004-102">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>
<span data-ttu-id="be004-103">Řízení přístupu k prostředkům v počítači domény Windows je úloha základní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="be004-103">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="be004-104">Například pouze určití uživatelé by měl moct prohlížet citlivá data, jako je například mzdové informace.</span><span class="sxs-lookup"><span data-stu-id="be004-104">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="be004-105">Toto téma vysvětluje, jak omezit přístup k metodě tak náročné, do které uživatel patří do předdefinované skupiny.</span><span class="sxs-lookup"><span data-stu-id="be004-105">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="be004-106">Pracovní ukázku najdete v tématu [autorizace přístupu k operacím služby](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="be004-106">For a working sample, see [Authorizing Access to Service Operations](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="be004-107">Úloha se skládá ze dvou samostatných postupů.</span><span class="sxs-lookup"><span data-stu-id="be004-107">The task consists of two separate procedures.</span></span> <span data-ttu-id="be004-108">První skupině vytvoří a naplní ho s uživateli.</span><span class="sxs-lookup"><span data-stu-id="be004-108">The first creates the group and populates it with users.</span></span> <span data-ttu-id="be004-109">Druhá <xref:System.Security.Permissions.PrincipalPermissionAttribute> tak, aby určovala skupině.</span><span class="sxs-lookup"><span data-stu-id="be004-109">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="be004-110">Vytvoření skupiny Windows</span><span class="sxs-lookup"><span data-stu-id="be004-110">To create a Windows group</span></span>  
  
1. <span data-ttu-id="be004-111">Otevřít **Správa počítače** konzoly.</span><span class="sxs-lookup"><span data-stu-id="be004-111">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="be004-112">Na levém panelu klikněte na tlačítko **místní uživatelé a skupiny**.</span><span class="sxs-lookup"><span data-stu-id="be004-112">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="be004-113">Klikněte pravým tlačítkem na **skupiny**a klikněte na tlačítko **nová skupina**.</span><span class="sxs-lookup"><span data-stu-id="be004-113">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="be004-114">V **název skupiny** zadejte název nové skupiny.</span><span class="sxs-lookup"><span data-stu-id="be004-114">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="be004-115">V **popis** zadejte popis nové skupiny.</span><span class="sxs-lookup"><span data-stu-id="be004-115">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="be004-116">Klikněte na tlačítko **přidat** tlačítko pro přidání nových členů do skupiny.</span><span class="sxs-lookup"><span data-stu-id="be004-116">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="be004-117">Pokud sami přidali do skupiny a chcete ho testovat následující kód, musíte počítač odhlásit a znovu přihlásit, aby se součástí skupiny.</span><span class="sxs-lookup"><span data-stu-id="be004-117">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="be004-118">Na vyžádání členství uživatelů</span><span class="sxs-lookup"><span data-stu-id="be004-118">To demand user membership</span></span>  
  
1. <span data-ttu-id="be004-119">Otevřete soubor kódu služby Windows Communication Foundation (WCF), která obsahuje kód kontraktu služby implementované.</span><span class="sxs-lookup"><span data-stu-id="be004-119">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="be004-120">Další informace o implementaci kontraktu a najdete v tématu [implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="be004-120">For more information about implementing a contract, see [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="be004-121">Použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut pro každou metodu, která musí být omezeno na konkrétní skupinu.</span><span class="sxs-lookup"><span data-stu-id="be004-121">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="be004-122">Nastavte <xref:System.Security.Permissions.SecurityAttribute.Action%2A> vlastnost <xref:System.Security.Permissions.SecurityAction.Demand> a <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> nastavte název skupiny.</span><span class="sxs-lookup"><span data-stu-id="be004-122">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="be004-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="be004-123">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="be004-124">Pokud použijete <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut na smlouvu <xref:System.Security.SecurityException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="be004-124">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="be004-125">Lze použít pouze atribut na úrovni metody.</span><span class="sxs-lookup"><span data-stu-id="be004-125">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="be004-126">Použití certifikátu pro řízení přístupu k metodě</span><span class="sxs-lookup"><span data-stu-id="be004-126">Using a Certificate to Control Access to a Method</span></span>  
 <span data-ttu-id="be004-127">Můžete také použít `PrincipalPermissionAttribute` třídy pro řízení přístupu k metodu, pokud typ pověření klienta je certifikát.</span><span class="sxs-lookup"><span data-stu-id="be004-127">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="be004-128">Chcete-li to provést, musí mít předmětu a kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="be004-128">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="be004-129">Pokud chcete prozkoumat certifikát pro jeho vlastnosti, přečtěte si téma [jak: Zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="be004-129">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="be004-130">Hodnoty kryptografického otisku, najdete v tématu [jak: Načtení kryptografického otisku certifikátu](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="be004-130">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="be004-131">Řízení přístupu k použití certifikátu</span><span class="sxs-lookup"><span data-stu-id="be004-131">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="be004-132">Použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> třídy chcete omezit přístup k metodě.</span><span class="sxs-lookup"><span data-stu-id="be004-132">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="be004-133">Nastavte akci atribut, který chcete <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be004-133">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="be004-134">Nastavte `Name` nastavte na řetězec, který se skládá z názvu předmětu a kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="be004-134">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="be004-135">Oddělení dvě hodnoty středník a mezeru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="be004-135">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="be004-136">Nastavte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> jak je znázorněno v následujícím příkladu konfigurace:</span><span class="sxs-lookup"><span data-stu-id="be004-136">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="be004-137">Tuto hodnotu nastavíte na `UseAspNetRoles` znamená, že `Name` vlastnost `PrincipalPermissionAttribute` se použije k provádění porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="be004-137">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="be004-138">Když je certifikát použit jako pověření klienta, ve výchozím nastavení WCF zřetězí běžný název certifikátu a kryptografický otisk oddělte středníkem. Chcete-li vytvořit jedinečnou hodnotu pro klienta primární identity.</span><span class="sxs-lookup"><span data-stu-id="be004-138">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="be004-139">S `UseAspNetRoles` nastavit jako `PrincipalPermissionMode` ve službě, tato hodnota primární identity je ve srovnání s `Name` hodnota vlastnosti k určení oprávnění uživatele.</span><span class="sxs-lookup"><span data-stu-id="be004-139">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="be004-140">Můžete také nastavit při vytváření služby v místním prostředí, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastností v kódu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="be004-140">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="be004-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be004-141">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="be004-142">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="be004-142">Authorizing Access to Service Operations</span></span>](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="be004-143">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="be004-143">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="be004-144">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="be004-144">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
