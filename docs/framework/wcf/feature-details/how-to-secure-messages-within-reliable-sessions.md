---
title: 'Postupy: Zabezpečené zprávy ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1592c9429e6cd425b86fa2b72bfebe977e18b048
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505079"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Postupy: Zabezpečené zprávy ve spolehlivých relacích

Toto téma popisuje kroky potřebné k povolení zabezpečení na úrovni zprávy ve spolehlivých relacích pomocí jedné vazby poskytované systémem, které podporují tyto relace, ale není ve výchozím nastavení, které si vyměňují zprávy. Povolení zabezpečené a spolehlivé relace imperativně pomocí kódu nebo deklarativně v konfiguračním souboru. Tento postup používá konfiguračních souborů klienta a služby umožňuje zabezpečené a spolehlivé relace.

Tento postup se skládá ze tří následujících klíčových úlohách:

1. Zadejte, že klient a služba výměna zpráv ve spolehlivých relacích.

1. Vyžadují zabezpečení na úrovni zprávy ve spolehlivých relacích.

1. Určení typu pověření klienta, který klient musí použít k ověření ve službě.

Je důležité v první úloze, která obsahují element konfigurace koncového bodu `bindingConfiguration` atribut, který odkazuje na konfiguraci vazby s názvem (v tomto příkladu) `MessageSecurity`. [  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) konfigurační prvek pak odkazuje na tento název a povolit tak, že nastavíte spolehlivé relace `enabled` atribut [  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elementu `true`. Může vyžadovat, že záruky objednané dodání jsou k dispozici ve spolehlivých relacích tak, že nastavíte `ordered` atribut `true`.

Zdroj kopie v příkladu, na kterém je založen tento postup konfigurace najdete v článku [spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

Základní položky druhý úkol můžete provést tak, že nastavíte `mode` atribut  **\<zabezpečení >** obsažených v elementu  **\<vazby >** prvek klienta a služby do `Message`.

Základní položky třetí úloh můžete provést tak, že nastavíte `clientCredentialType` atribut  **\<zpráva >** obsažených v elementu  **\<zabezpečení >** prvek klienta a služby do `Certificate`.

> [!NOTE]
> Při používání zabezpečení zpráv s spolehlivé relace, spolehlivé zasílání zpráv pokus o ověření neověřené klientské dokud namísto vyvolání výjimky po prvním selhání dojde k vypršení časového limitu.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Nakonfigurovat službu pomocí WSHttpBinding používat spolehlivé relace

Tento postup je popsaný v [postupy: výměna zprávy v rámci stabilní relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace klienta s WSHttpBinding používat spolehlivé relace

Tento postup je popsaný v [postupy: výměna zprávy v rámci stabilní relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Nastavte režim a nebyl typ ClientCredentialType v konfiguraci

1. Přidat element příslušnou datovou vazbu [  **\<vazby >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element konfiguračního souboru. Následující příklad přidá [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.

1. Přidat  **\<vazby >** elementu a nastavte jeho `name` atribut na odpovídající hodnotu. V příkladu se používá název `MessageSecurity`.

1. Přidat  **\<zabezpečení >** elementu a nastavte `mode` atribut `Message`.

1. V rámci  **\<zabezpečení >** elementu, přidat  **\<zpráva >** elementu a nastavte `clientCredentialType` atribut `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
