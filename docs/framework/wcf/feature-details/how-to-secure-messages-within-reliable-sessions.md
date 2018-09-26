---
title: 'Postupy: Zabezpečené zprávy ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
author: BrucePerlerMS
ms.openlocfilehash: f3269dc96dee2d534a8dd6677abeb6afae8776bd
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47115081"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="ee425-102">Postupy: Zabezpečené zprávy ve spolehlivých relacích</span><span class="sxs-lookup"><span data-stu-id="ee425-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="ee425-103">Toto téma popisuje kroky potřebné k povolení zabezpečení na úrovni zprávy ve spolehlivých relacích pomocí jedné vazby poskytované systémem, které podporují tyto relace, ale není ve výchozím nastavení, které si vyměňují zprávy.</span><span class="sxs-lookup"><span data-stu-id="ee425-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="ee425-104">Povolení zabezpečené a spolehlivé relace imperativně pomocí kódu nebo deklarativně v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ee425-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="ee425-105">Tento postup používá konfiguračních souborů klienta a služby umožňuje zabezpečené a spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="ee425-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="ee425-106">Tento postup se skládá ze tří následujících klíčových úlohách:</span><span class="sxs-lookup"><span data-stu-id="ee425-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="ee425-107">Zadejte, že klient a služba výměna zpráv ve spolehlivých relacích.</span><span class="sxs-lookup"><span data-stu-id="ee425-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="ee425-108">Vyžadují zabezpečení na úrovni zprávy ve spolehlivých relacích.</span><span class="sxs-lookup"><span data-stu-id="ee425-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="ee425-109">Určení typu pověření klienta, který klient musí použít k ověření ve službě.</span><span class="sxs-lookup"><span data-stu-id="ee425-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="ee425-110">Je důležité v první úloze, která obsahují element konfigurace koncového bodu `bindingConfiguration` atribut, který odkazuje na konfiguraci vazby s názvem (v tomto příkladu) `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="ee425-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="ee425-111">[  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) konfigurační prvek pak odkazuje na tento název a povolit tak, že nastavíte spolehlivé relace `enabled` atribut [  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="ee425-111">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="ee425-112">Může vyžadovat, že záruky objednané dodání jsou k dispozici ve spolehlivých relacích tak, že nastavíte `ordered` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="ee425-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="ee425-113">Zdroj kopie v příkladu, na kterém je založen tento postup konfigurace najdete v článku [spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="ee425-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="ee425-114">Základní položky druhý úkol můžete provést tak, že nastavíte `mode` atribut  **\<zabezpečení >** obsažených v elementu  **\<vazby >** prvek klienta a služby do `Message`.</span><span class="sxs-lookup"><span data-stu-id="ee425-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="ee425-115">Základní položky třetí úloh můžete provést tak, že nastavíte `clientCredentialType` atribut  **\<zpráva >** obsažených v elementu  **\<zabezpečení >** prvek klienta a služby do `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="ee425-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="ee425-116">Při používání zabezpečení zpráv s spolehlivé relace, spolehlivé zasílání zpráv pokus o ověření neověřené klientské dokud namísto vyvolání výjimky po prvním selhání dojde k vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="ee425-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="ee425-117">Nakonfigurovat službu pomocí WSHttpBinding používat spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="ee425-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="ee425-118">Tento postup je popsaný v [postupy: výměna zprávy v rámci stabilní relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="ee425-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="ee425-119">Konfigurace klienta s WSHttpBinding používat spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="ee425-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="ee425-120">Tento postup je popsaný v [postupy: výměna zprávy v rámci stabilní relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="ee425-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="ee425-121">Nastavte režim a nebyl typ ClientCredentialType v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="ee425-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="ee425-122">Přidat element příslušnou datovou vazbu [  **\<vazby >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ee425-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="ee425-123">Následující příklad přidá [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ee425-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="ee425-124">Přidat  **\<vazby >** elementu a nastavte jeho `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ee425-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="ee425-125">V příkladu se používá název `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="ee425-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="ee425-126">Přidat  **\<zabezpečení >** elementu a nastavte `mode` atribut `Message`.</span><span class="sxs-lookup"><span data-stu-id="ee425-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="ee425-127">V rámci  **\<zabezpečení >** elementu, přidat  **\<zpráva >** elementu a nastavte `clientCredentialType` atribut `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="ee425-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
