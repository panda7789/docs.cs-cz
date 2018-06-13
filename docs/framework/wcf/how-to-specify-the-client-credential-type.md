---
title: 'Postupy: Určení typu pověření klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: 5e1ff85d8a0bd45c87786f98c2cafe06472052b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499334"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="31947-102">Postupy: Určení typu pověření klienta</span><span class="sxs-lookup"><span data-stu-id="31947-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="31947-103">Po nastavení režimu zabezpečení (přenos nebo zpráv), máte možnost nastavení klienta typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="31947-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="31947-104">Tato vlastnost určuje, jaký typ přihlašovacích údajů klient musí poskytnout službě pro ověření.</span><span class="sxs-lookup"><span data-stu-id="31947-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="31947-105">Další informace o nastavení režimu zabezpečení (nezbytným krokem před nastavením klienta typ přihlašovacích údajů) najdete v tématu [postupy: nastavení režimu zabezpečení](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="31947-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="31947-106">Chcete-li nastavit typ přihlašovacích údajů klienta v kódu</span><span class="sxs-lookup"><span data-stu-id="31947-106">To set the client credential type in code</span></span>  
  
1.  <span data-ttu-id="31947-107">Vytvoření instance vazby, který bude používán službou.</span><span class="sxs-lookup"><span data-stu-id="31947-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="31947-108">Tento příklad používá <xref:System.ServiceModel.WSHttpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="31947-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2.  <span data-ttu-id="31947-109">Nastavte <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="31947-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="31947-110">Tento příklad používá režim zprávy.</span><span class="sxs-lookup"><span data-stu-id="31947-110">This example uses the Message mode.</span></span>  
  
3.  <span data-ttu-id="31947-111">Nastavte <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="31947-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="31947-112">Tento příklad nastaví ho na použití ověřování systému Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="31947-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="31947-113">Chcete-li nastavit typ přihlašovacích údajů klienta v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="31947-113">To set the client credential type in configuration</span></span>  
  
1.  <span data-ttu-id="31947-114">Přidat [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="31947-114">Add a [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2.  <span data-ttu-id="31947-115">Jako podřízený element přidat [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span><span class="sxs-lookup"><span data-stu-id="31947-115">As a child element, add a [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3.  <span data-ttu-id="31947-116">Přidejte příslušné vazby.</span><span class="sxs-lookup"><span data-stu-id="31947-116">Add an appropriate binding.</span></span> <span data-ttu-id="31947-117">Tento příklad používá [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="31947-117">This example uses the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4.  <span data-ttu-id="31947-118">Přidat [ \<vazby >](../../../docs/framework/misc/binding.md) elementu a sadu `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="31947-118">Add a [\<binding>](../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="31947-119">Tento příklad používá název "SecureBinding".</span><span class="sxs-lookup"><span data-stu-id="31947-119">This example uses the name "SecureBinding".</span></span>  
  
5.  <span data-ttu-id="31947-120">Přidat `<security>` vazby.</span><span class="sxs-lookup"><span data-stu-id="31947-120">Add a `<security>` binding.</span></span> <span data-ttu-id="31947-121">Nastavte `mode` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="31947-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="31947-122">Tento příklad ji nastaví na `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="31947-122">This example sets it to `"Message"`.</span></span>  
  
6.  <span data-ttu-id="31947-123">Přidat buď `<message>` nebo `<transport>` elementu, počítáno od režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="31947-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="31947-124">Nastavte `clientCredentialType` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="31947-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="31947-125">Tento příklad používá `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="31947-125">This example uses `"Windows"`.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="31947-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="31947-126">See Also</span></span>  
 [<span data-ttu-id="31947-127">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="31947-127">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="31947-128">Postupy: Nastavení režimu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="31947-128">How to: Set the Security Mode</span></span>](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
