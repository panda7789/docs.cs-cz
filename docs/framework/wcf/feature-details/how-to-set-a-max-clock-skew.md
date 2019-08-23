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
ms.openlocfilehash: 3bcd128e6e9f53f662dd3fc99336b5b45faebf5f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943120"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="4f382-102">Postupy: Nastvení hodnoty vlastnosti MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="4f382-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="4f382-103">V případě, že se nastavení hodin ve dvou počítačích liší, je možné časově kritické funkce dekolejnice.</span><span class="sxs-lookup"><span data-stu-id="4f382-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="4f382-104">Pro zmírnění této možnosti můžete nastavit `MaxClockSkew` vlastnost <xref:System.TimeSpan>na.</span><span class="sxs-lookup"><span data-stu-id="4f382-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="4f382-105">Tato vlastnost je k dispozici na dvou třídách:</span><span class="sxs-lookup"><span data-stu-id="4f382-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="4f382-106">V případě zabezpečené konverzace je třeba provést změny `MaxClockSkew` vlastnosti při zavedení služby nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="4f382-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="4f382-107">K tomu je nutné nastavit vlastnost <xref:System.ServiceModel.Channels.SecurityBindingElement> vrácenou <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> vlastností.</span><span class="sxs-lookup"><span data-stu-id="4f382-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="4f382-108">Chcete-li změnit vlastnost u jedné z vazeb poskytovaných systémem, je nutné najít prvek vazby zabezpečení v kolekci vazeb a nastavit `MaxClockSkew` vlastnost na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4f382-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="4f382-109">Dvě třídy jsou odvozeny <xref:System.ServiceModel.Channels.SecurityBindingElement>z <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> : <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>a.</span><span class="sxs-lookup"><span data-stu-id="4f382-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="4f382-110">Při načítání vazby zabezpečení z kolekce je třeba přetypovat na jeden z těchto typů, aby bylo možné správně nastavit `MaxClockSkew` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4f382-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="4f382-111">Následující příklad používá <xref:System.ServiceModel.WSHttpBinding>, který <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>používá.</span><span class="sxs-lookup"><span data-stu-id="4f382-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="4f382-112">Seznam, který určuje typ vazby zabezpečení, který se má použít v každé vazbě poskytované systémem, najdete v tématu [vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="4f382-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="4f382-113">Vytvoření vlastní vazby s novou hodnotou asymetrie hodin v kódu</span><span class="sxs-lookup"><span data-stu-id="4f382-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="4f382-114">Do kódu přidejte odkazy na následující obory názvů: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>a <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="4f382-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="4f382-115">Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4f382-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="4f382-116">Vytvořte novou instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídy <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="4f382-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="4f382-117">K nalezení elementu vazby zabezpečení <xref:System.ServiceModel.Channels.BindingElementCollection> použijte metodutřídy.<xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A></span><span class="sxs-lookup"><span data-stu-id="4f382-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="4f382-118">Při použití <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody přetypovat na skutečný typ.</span><span class="sxs-lookup"><span data-stu-id="4f382-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="4f382-119">Níže uvedený příklad přetypování na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typ.</span><span class="sxs-lookup"><span data-stu-id="4f382-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="4f382-120"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> Nastavte vlastnost na elementu vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4f382-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="4f382-121"><xref:System.ServiceModel.ServiceHost> Vytvořte s příslušným typem služby a základní adresou.</span><span class="sxs-lookup"><span data-stu-id="4f382-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="4f382-122">Použijte metodu pro přidání koncového bodu a <xref:System.ServiceModel.Channels.CustomBinding>zahrnutí. <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A></span><span class="sxs-lookup"><span data-stu-id="4f382-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="4f382-123">Nastavení MaxClockSkew v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="4f382-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="4f382-124">Vytvořte > CustomBinding v části > elementu [ Bindings.\<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4f382-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="4f382-125">Vytvořte vazbu [ >elementuanastavteatributnaodpovídajícíhodnotu.\<](../../../../docs/framework/misc/binding.md) `name`</span><span class="sxs-lookup"><span data-stu-id="4f382-125">Create a [\<binding>](../../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="4f382-126">Následující příklad nastaví na `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="4f382-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="4f382-127">Přidejte element Encoding.</span><span class="sxs-lookup"><span data-stu-id="4f382-127">Add an encoding element.</span></span> <span data-ttu-id="4f382-128">Následující příklad přidá [ \<> textMessageEncoding](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="4f382-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="4f382-129">Přidejte element [Security > a nastavte atribut na příslušné nastavení. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) `authenticationMode`</span><span class="sxs-lookup"><span data-stu-id="4f382-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="4f382-130">Následující příklad nastaví atribut tak `Kerberos` , aby určoval, že služba používá ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4f382-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="4f382-131">Přidejte > `maxClockSkew` `"##:##:##"`localServiceSettings a nastavte atribut na hodnotu ve formě. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="4f382-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="4f382-132">V následujícím příkladu se nastaví na 7 minut.</span><span class="sxs-lookup"><span data-stu-id="4f382-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="4f382-133">Volitelně přidejte [ \<> localServiceSettings](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavte `maxClockSkew` atribut na příslušné nastavení.</span><span class="sxs-lookup"><span data-stu-id="4f382-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="4f382-134">Přidejte transportní element.</span><span class="sxs-lookup"><span data-stu-id="4f382-134">Add a transport element.</span></span> <span data-ttu-id="4f382-135">Následující příklad používá [ \<> HttpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="4f382-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="4f382-136">Pro zabezpečenou konverzaci musí být nastavení zabezpečení provedeno při spuštění v [ \<elementu secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) .</span><span class="sxs-lookup"><span data-stu-id="4f382-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f382-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f382-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4f382-138">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="4f382-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
