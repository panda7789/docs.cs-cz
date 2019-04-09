---
title: 'Postupy: Nastvení hodnoty vlastnosti MaxClockSkew'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: e487da6316ec381c2009ee33575848dd80df8ab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076625"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="a7d90-102">Postupy: Nastvení hodnoty vlastnosti MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="a7d90-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="a7d90-103">Kritického pro čas funkce můžete kolejnic, pokud se nastavení hodin na dva počítače liší.</span><span class="sxs-lookup"><span data-stu-id="a7d90-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="a7d90-104">Pro zmírnění této možnosti můžete nastavit `MaxClockSkew` vlastnost <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="a7d90-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="a7d90-105">Tato vlastnost je k dispozici na dvou tříd:</span><span class="sxs-lookup"><span data-stu-id="a7d90-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7d90-106">Důležité pro zabezpečené konverzace, změní `MaxClockSkew` vlastnost musí vzít v úvahu si připravili službu nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="a7d90-106">Important   For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="a7d90-107">Chcete-li to provést, musíte nastavit vlastnost na <xref:System.ServiceModel.Channels.SecurityBindingElement> vrácených <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7d90-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span></span>  
  
 <span data-ttu-id="a7d90-108">Chcete-li změnit vlastnosti na jednom z vazeb poskytovaných systémem, musíte najít element vazby zabezpečení v kolekci vazby a nastavit `MaxClockSkew` vlastnost na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a7d90-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="a7d90-109">Dvě třídy odvozovat <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="a7d90-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="a7d90-110">Při načítání vazby zabezpečení z kolekce, musíte přetypovat na jeden z těchto typů aby bylo možné správně nastavená `MaxClockSkew` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a7d90-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="a7d90-111">Následující příklad používá <xref:System.ServiceModel.WSHttpBinding>, který používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="a7d90-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="a7d90-112">Seznam, který určuje, který typ zabezpečení vazby pro použití v jednotlivých vazeb poskytovaných systémem najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a7d90-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="a7d90-113">K vytvoření vlastní vazby s novou hodinami zkosení hodnotu v kódu</span><span class="sxs-lookup"><span data-stu-id="a7d90-113">To create a custom binding with a new clock skew value in code</span></span>  
  
1.  > [!WARNING]
    >  <span data-ttu-id="a7d90-114">Všimněte si přidat odkazy na následující obory názvů v kódu: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, a <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="a7d90-114">Note   Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
     <span data-ttu-id="a7d90-115">Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte jeho režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="a7d90-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
2.  <span data-ttu-id="a7d90-116">Vytvořit novou instanci třídy <xref:System.ServiceModel.Channels.BindingElementCollection> třídy voláním <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a7d90-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="a7d90-117">Použití <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metodu <xref:System.ServiceModel.Channels.BindingElementCollection> třídy najít element vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a7d90-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4.  <span data-ttu-id="a7d90-118">Při použití <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metoda přetypovat na skutečný typ.</span><span class="sxs-lookup"><span data-stu-id="a7d90-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="a7d90-119">V příkladu níže přetypování <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typu.</span><span class="sxs-lookup"><span data-stu-id="a7d90-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5.  <span data-ttu-id="a7d90-120">Nastavte <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> vlastnosti prvku vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a7d90-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6.  <span data-ttu-id="a7d90-121">Vytvoření <xref:System.ServiceModel.ServiceHost> typ a základní adresou příslušnou službu.</span><span class="sxs-lookup"><span data-stu-id="a7d90-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7.  <span data-ttu-id="a7d90-122">Použití <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> způsob přidání koncového bodu a zahrnout <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="a7d90-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="a7d90-123">Chcete-li nastavit maxclockskew – v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="a7d90-123">To set the MaxClockSkew in configuration</span></span>  
  
1.  <span data-ttu-id="a7d90-124">Vytvoření [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) v [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekce prvku.</span><span class="sxs-lookup"><span data-stu-id="a7d90-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2.  <span data-ttu-id="a7d90-125">Vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a7d90-125">Create a [\<binding>](../../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="a7d90-126">Následující příklad nastaví na `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="a7d90-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3.  <span data-ttu-id="a7d90-127">Přidáte element kódování.</span><span class="sxs-lookup"><span data-stu-id="a7d90-127">Add an encoding element.</span></span> <span data-ttu-id="a7d90-128">Následující příklad přidá [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="a7d90-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4.  <span data-ttu-id="a7d90-129">Přidat [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu a nastavte `authenticationMode` atribut se vhodným nastavením.</span><span class="sxs-lookup"><span data-stu-id="a7d90-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="a7d90-130">V následujícím příkladu nastavte atribut na `Kerberos` určující, zda služba ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="a7d90-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5.  <span data-ttu-id="a7d90-131">Přidat [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavit `maxClockSkew` atribut na hodnotu ve formě `"##:##:##"`.</span><span class="sxs-lookup"><span data-stu-id="a7d90-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="a7d90-132">Následující příklad nastaví ji na 7 minut.</span><span class="sxs-lookup"><span data-stu-id="a7d90-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="a7d90-133">Volitelně můžete přidat [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavit `maxClockSkew` atribut se vhodným nastavením.</span><span class="sxs-lookup"><span data-stu-id="a7d90-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6.  <span data-ttu-id="a7d90-134">Přidáte element přenosu.</span><span class="sxs-lookup"><span data-stu-id="a7d90-134">Add a transport element.</span></span> <span data-ttu-id="a7d90-135">Následující příklad používá [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="a7d90-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7.  <span data-ttu-id="a7d90-136">Pro zabezpečené konverzace, nastavení zabezpečení se musí vyskytovat na spuštění v [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a7d90-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a7d90-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7d90-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a7d90-138">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a7d90-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
