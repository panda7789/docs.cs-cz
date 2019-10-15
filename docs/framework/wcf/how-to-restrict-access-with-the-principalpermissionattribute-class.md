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
ms.openlocfilehash: 93268be4b04ec6824ed7ecab070f28ddf40f8831
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320943"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="9716f-102">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="9716f-102">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>
<span data-ttu-id="9716f-103">Řízení přístupu k prostředkům v počítači se systémem Windows je základní úloha zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9716f-103">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="9716f-104">Například jenom někteří uživatelé by měli být schopni zobrazit citlivá data, jako jsou mzdové údaje.</span><span class="sxs-lookup"><span data-stu-id="9716f-104">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="9716f-105">Toto téma vysvětluje, jak omezit přístup k metodě tím, že vyžaduje, aby uživatel patřil do předdefinované skupiny.</span><span class="sxs-lookup"><span data-stu-id="9716f-105">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="9716f-106">Pracovní ukázku najdete v tématu [autorizace přístupu k operacím služby](./samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9716f-106">For a working sample, see [Authorizing Access to Service Operations](./samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="9716f-107">Úkol se skládá ze dvou samostatných postupů.</span><span class="sxs-lookup"><span data-stu-id="9716f-107">The task consists of two separate procedures.</span></span> <span data-ttu-id="9716f-108">První vytvoří skupinu a naplní ji uživateli.</span><span class="sxs-lookup"><span data-stu-id="9716f-108">The first creates the group and populates it with users.</span></span> <span data-ttu-id="9716f-109">Druhý používá třídu <xref:System.Security.Permissions.PrincipalPermissionAttribute> k určení skupiny.</span><span class="sxs-lookup"><span data-stu-id="9716f-109">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="9716f-110">Vytvoření skupiny systému Windows</span><span class="sxs-lookup"><span data-stu-id="9716f-110">To create a Windows group</span></span>  
  
1. <span data-ttu-id="9716f-111">Otevřete konzolu **Správa počítače** .</span><span class="sxs-lookup"><span data-stu-id="9716f-111">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="9716f-112">Na levém panelu klikněte na **místní uživatelé a skupiny**.</span><span class="sxs-lookup"><span data-stu-id="9716f-112">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="9716f-113">Klikněte pravým tlačítkem na **skupiny**a pak klikněte na **Nová skupina**.</span><span class="sxs-lookup"><span data-stu-id="9716f-113">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="9716f-114">Do pole **název skupiny** zadejte název nové skupiny.</span><span class="sxs-lookup"><span data-stu-id="9716f-114">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="9716f-115">Do pole **Popis** zadejte popis nové skupiny.</span><span class="sxs-lookup"><span data-stu-id="9716f-115">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="9716f-116">Kliknutím na tlačítko **Přidat** přidejte do skupiny nové členy.</span><span class="sxs-lookup"><span data-stu-id="9716f-116">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="9716f-117">Pokud jste do skupiny přidali sami sebe a chcete otestovat následující kód, musíte se odhlásit od počítače a znovu se přihlásit, aby byl zahrnutý do skupiny.</span><span class="sxs-lookup"><span data-stu-id="9716f-117">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="9716f-118">Pro vyžádání členství uživatele</span><span class="sxs-lookup"><span data-stu-id="9716f-118">To demand user membership</span></span>  
  
1. <span data-ttu-id="9716f-119">Otevřete soubor kódu Windows Communication Foundation (WCF), který obsahuje implementovaný kód kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="9716f-119">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="9716f-120">Další informace o implementaci kontraktu najdete v tématu [implementace kontraktů služeb](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9716f-120">For more information about implementing a contract, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="9716f-121">Použijte atribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> pro každou metodu, která musí být omezena na konkrétní skupinu.</span><span class="sxs-lookup"><span data-stu-id="9716f-121">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="9716f-122">Nastavte vlastnost <xref:System.Security.Permissions.SecurityAttribute.Action%2A> na hodnotu <xref:System.Security.Permissions.SecurityAction.Demand> a vlastnost <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> na název skupiny.</span><span class="sxs-lookup"><span data-stu-id="9716f-122">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="9716f-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9716f-123">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="9716f-124">Použijete-li atribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> u kontraktu, bude vyvolána hodnota <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="9716f-124">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="9716f-125">Atribut lze použít pouze na úrovni metody.</span><span class="sxs-lookup"><span data-stu-id="9716f-125">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="9716f-126">Použití certifikátu pro řízení přístupu k metodě</span><span class="sxs-lookup"><span data-stu-id="9716f-126">Using a Certificate to Control Access to a Method</span></span>  
 <span data-ttu-id="9716f-127">Můžete také použít třídu `PrincipalPermissionAttribute` k řízení přístupu k metodě, pokud je typ přihlašovacích údajů klienta certifikát.</span><span class="sxs-lookup"><span data-stu-id="9716f-127">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="9716f-128">K tomu je potřeba, abyste měli předmět a kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="9716f-128">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="9716f-129">Chcete-li si prohlédnout certifikát pro jeho vlastnosti, přečtěte si téma [Postup: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="9716f-129">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="9716f-130">Chcete-li zjistit hodnotu kryptografického otisku, přečtěte si téma [How to: Načtení kryptografického otisku certifikátu](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="9716f-130">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="9716f-131">Řízení přístupu pomocí certifikátu</span><span class="sxs-lookup"><span data-stu-id="9716f-131">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="9716f-132">Použijte třídu <xref:System.Security.Permissions.PrincipalPermissionAttribute> na metodu, ke které chcete omezit přístup.</span><span class="sxs-lookup"><span data-stu-id="9716f-132">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="9716f-133">Nastavte akci atributu na <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9716f-133">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="9716f-134">Nastavte vlastnost `Name` na řetězec, který se skládá z názvu subjektu a otisku certifikátu.</span><span class="sxs-lookup"><span data-stu-id="9716f-134">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="9716f-135">Tyto dvě hodnoty oddělte středníkem a mezerou, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9716f-135">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="9716f-136">Nastavte vlastnost <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> na <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, jak je znázorněno v následujícím příkladu konfigurace:</span><span class="sxs-lookup"><span data-stu-id="9716f-136">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="9716f-137">Nastavení této hodnoty na `UseAspNetRoles` znamená, že pro porovnání řetězců se použije vlastnost `Name` `PrincipalPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="9716f-137">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="9716f-138">Pokud se certifikát používá jako přihlašovací údaje klienta, ve výchozím nastavení služba WCF zřetězí běžný název certifikátu a kryptografický otisk středníkem, aby vytvořil jedinečnou hodnotu pro primární identitu klienta.</span><span class="sxs-lookup"><span data-stu-id="9716f-138">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="9716f-139">Když je u služby `UseAspNetRoles` nastavená jako `PrincipalPermissionMode`, hodnota této primární identity se porovná s hodnotou vlastnosti `Name` a určí přístupová práva uživatele.</span><span class="sxs-lookup"><span data-stu-id="9716f-139">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="9716f-140">Případně při vytváření samoobslužné služby nastavte vlastnost <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> v kódu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="9716f-140">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9716f-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9716f-141">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="9716f-142">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="9716f-142">Authorizing Access to Service Operations</span></span>](./samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="9716f-143">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9716f-143">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="9716f-144">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="9716f-144">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
