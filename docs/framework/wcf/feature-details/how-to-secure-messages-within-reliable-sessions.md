---
title: "Postupy: Zabezpečené zprávy ve spolehlivých relacích"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2604b9dacf11b9971b10d23d9a807092ddf07830
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="1bcd0-102">Postupy: Zabezpečené zprávy ve spolehlivých relacích</span><span class="sxs-lookup"><span data-stu-id="1bcd0-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="1bcd0-103">Toto téma popisuje kroky potřebné k povolení zabezpečení na úrovni zpráv pro zprávy vyměňují ve spolehlivých relacích pomocí jedné vazby poskytované systémem, které podporují tyto relace, ale není ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="1bcd0-104">Povolte zabezpečené a spolehlivé relace imperativní pomocí kódu nebo deklarativně v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="1bcd0-105">Tento postup používá konfigurační soubory, které klient a služba Povolit zabezpečené a spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="1bcd0-106">Tento postup se skládá ze tří následujících klíčových úlohách:</span><span class="sxs-lookup"><span data-stu-id="1bcd0-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="1bcd0-107">Zadejte, zda klient a služba výměna zpráv ve spolehlivých relacích.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="1bcd0-108">Vyžadovat zabezpečení na úrovni zpráv v rámci spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="1bcd0-109">Zadejte typ pověření klienta, který klient musí použít k ověření u služby.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="1bcd0-110">Je důležité v první úloze, které obsahují element konfigurace koncového bodu `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem (v tomto příkladu) `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="1bcd0-111">[  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) konfigurační prvek pak odkazuje tento název pro nastavení Povolit spolehlivé relace `enabled` atribut [  **\<reliableSession >** ](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element `true`.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-111">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="1bcd0-112">Můžete vyžadovat, aby záruky doručení jsou k dispozici ve spolehlivých relacích nastavením `ordered` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="1bcd0-113">Zdroj kopii příklad, na kterých je založena tento postup konfigurace, najdete v článku [spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="1bcd0-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="1bcd0-114">Základní položky v druhé úloze se provádí nastavením `mode` atribut  **\<zabezpečení >** obsažené v elementu  **\<vazby >** Element klienta a služby `Message`.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="1bcd0-115">Základní položky třetí úlohy se provádí nastavením `clientCredentialType` atribut  **\<zpráva >** obsažené v elementu  **\<zabezpečení >** Element klienta a služby `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="1bcd0-116">Při použití zabezpečení zpráv s spolehlivé relace, spolehlivé zasílání zpráv pokus o ověření neověřené klienta, dokud místo došlo k výjimce při prvním selhání dojde k vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="1bcd0-117">Konfigurovat službu s WSHttpBinding používat spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="1bcd0-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="1bcd0-118">Tento postup je popsaný v [postup: Exchange zprávy v rámci spolehlivé relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="1bcd0-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="1bcd0-119">Konfigurace klienta s WSHttpBinding používat spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="1bcd0-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="1bcd0-120">Tento postup je popsaný v [postup: Exchange zprávy v rámci spolehlivé relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="1bcd0-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="1bcd0-121">Nastavte režim a ClientCredentialType v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="1bcd0-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="1bcd0-122">Přidat element do odpovídající vazby [  **\<vazby >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="1bcd0-123">Následující příklad přidá [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="1bcd0-124">Přidat  **\<vazby >** elementu a sadu jeho `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="1bcd0-125">Tento příklad používá název `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="1bcd0-126">Přidat  **\<zabezpečení >** elementu a sadu `mode` atribut `Message`.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="1bcd0-127">V rámci  **\<zabezpečení >** elementu, přidejte  **\<zpráva >** elementu a sadu `clientCredentialType` atribut `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="1bcd0-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
