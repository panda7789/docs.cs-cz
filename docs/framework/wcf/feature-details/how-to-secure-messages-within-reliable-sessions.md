---
title: 'Postupy: Zabezpečené zprávy ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: 306d0f96b5163fe5c24d270b4b9a7c1d3f499e7e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596952"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Postupy: Zabezpečené zprávy ve spolehlivých relacích

Toto téma popisuje kroky potřebné k povolení zabezpečení na úrovni zprávy pro zprávy vyměňované v rámci spolehlivé relace pomocí jedné z vazeb poskytovaných systémem, které podporují takovou relaci, ale nejsou ve výchozím nastavení. Povolit zabezpečenou a spolehlivou relaci buď imperativně, pomocí kódu nebo deklarativního v konfiguračním souboru. Tento postup využívá konfigurační soubory klienta a služby k zajištění zabezpečené a spolehlivé relace.

Tento postup se skládá z následujících tří klíčových úloh:

1. Určete, že zprávy klienta a služby Exchange v rámci spolehlivé relace.

1. Vyžadovat zabezpečení na úrovni zpráv v rámci spolehlivé relace.

1. Zadejte typ přihlašovacích údajů klienta, který musí klient použít pro ověření u služby.

Je důležité v prvním úkolu, který prvek konfigurace koncového bodu obsahuje `bindingConfiguration` atribut, který odkazuje na konfiguraci vazby s názvem (v tomto příkladu) `MessageSecurity` . [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Prvek konfigurace pak na tento název odkazuje, aby povoloval spolehlivé relace nastavením `enabled` atributu [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) elementu na `true` . Můžete požadovat, aby seřazené záruky doručení byly dostupné v rámci spolehlivé relace nastavením `ordered` atributu na `true` .

Zdrojovou kopii příkladu, na kterém je tato procedura Konfigurace založená, najdete v tématu [Spolehlivá relace WS](../samples/ws-reliable-session.md).

Základní položky druhé úlohy jsou provedeny nastavením `mode` atributu **\<security>** elementu obsaženého v **\<binding>** prvku klienta a služby na `Message` .

Podstatné položky třetí úlohy jsou provedeny nastavením `clientCredentialType` atributu **\<message>** elementu obsaženého v **\<security>** prvku klienta a služby na `Certificate` .

> [!NOTE]
> Při použití zabezpečení zpráv u spolehlivých relací se spolehlivé zasílání zpráv pokusí ověřit neověřeného klienta, dokud nedojde k vypršení časového limitu namísto vyvolání výjimky při prvním selhání.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace služby s WSHttpBinding pro použití spolehlivé relace

Tento postup je popsaný v tématu [Postupy: Výměna zpráv v rámci spolehlivé relace](how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace klienta s WSHttpBinding pro použití spolehlivé relace

Tento postup je popsaný v tématu [Postupy: Výměna zpráv v rámci spolehlivé relace](how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Nastavení režimu a ClientCredentialType v konfiguraci

1. Přidejte vhodný element vazby do [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) elementu konfiguračního souboru. Následující příklad přidá [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) prvek.

1. Přidejte **\<binding>** element a nastavte jeho `name` atribut na odpovídající hodnotu. V příkladu se používá název `MessageSecurity` .

1. Přidejte **\<security>** element a nastavte `mode` atribut na `Message` .

1. V rámci **\<security>** elementu přidejte **\<message>** element a nastavte `clientCredentialType` atribut na `Certificate` .

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
