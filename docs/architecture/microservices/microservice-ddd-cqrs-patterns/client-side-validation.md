---
title: Ověřování na straně klienta (ověřování v prezentačních vrstvách)
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Prozkoumejte klíčové koncepty ověřování na straně klienta.
ms.date: 10/08/2018
ms.openlocfilehash: 44c1e9fa280b19fcee87d4d1cdfcaa2ab9462f27
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988698"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Ověřování na straně klienta (ověřování v prezentačních vrstvách)

I v případě, že zdrojem pravdy je model domény a nakonec musíte mít ověření na úrovni modelu domény, ověření lze stále zpracovávat na úrovni modelu domény (na straně serveru) a na straně ui (na straně klienta).

Ověření na straně klienta je pro uživatele velkým pohodlím. To šetří čas, který by jinak strávit čekání na zpáteční cestu na server, který by mohl vrátit chyby ověření. Z obchodního hlediska, i několik zlomků sekund násobí stokrát každý den přidává až hodně času, nákladů a frustrace. Jednoduché a okamžité ověření umožňuje uživatelům pracovat efektivněji a vytvářet kvalitnější vstupy a výstupy.

Stejně jako model zobrazení a model domény se liší, zobrazení modelu ověřování a ověření modelu domény může být podobné, ale slouží jinému účelu. Pokud máte obavy o DRY (Don't Repeat Yourself princip), za to, že v tomto případě kód opětovné použití může také znamenat spojení, a v podnikových aplikacích je důležitější, aby pár straně serveru na straně klienta, než dodržovat princip DRY.

I při použití ověření na straně klienta byste měli vždy ověřit příkazy nebo vstupní dtovací v kódu serveru, protože serverová api jsou možným vektorem útoku. Obvykle, dělá obojí je vaše nejlepší sázka, protože pokud máte klientskou aplikaci, z hlediska Uživatelského rozhraní, to je nejlepší být proaktivní a nedovolit uživateli zadat neplatné informace.

Proto v kódu na straně klienta obvykle ověřit ViewModels. Můžete také ověřit výstup klienta DTO nebo příkazy před jejich odesláním do služeb.

Implementace ověření na straně klienta závisí na tom, jaký druh klientské aplikace vytváříte. Bude to jiné, pokud ověřujete data ve webové webové aplikaci MVC s většinou kódu v rozhraní .NET, webové aplikace SPA s tímto ověřením kódovaném v Jazyce JavaScript nebo TypeScript nebo mobilní aplikace kódovaná xamarinem a c#.

## <a name="additional-resources"></a>Další zdroje

### <a name="validation-in-xamarin-mobile-apps"></a>Ověření v mobilních aplikacích Xamarin

- **Ověřit zadávání textu a zobrazit chyby** \
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- **Zpětné volání ověření** \
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a>Ověření v aplikacích ASP.NET Core

- **Rick Anderson. Přidání ověření** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Ověření ve webových aplikacích SPA (Úhlové 2, TypeScript, JavaScript)

- **Ado Kukic. Ověřování formuláře úhlové 2** \
  <https://scotch.io/tutorials/angular-2-form-validation>

- **Ověření formuláře** \
  <https://angular.io/guide/form-validation>

- **Ověření.** Breeze dokumentace. \
  <https://breeze.github.io/doc-js/validation.html>

Stručně řečeno, jedná se o nejdůležitější pojmy, pokud jde o validaci:

- Entity a agregace by měly vynucovat vlastní konzistenci a být "vždy platné". Agregační kořeny jsou zodpovědné za konzistenci více entit v rámci stejného agregace.

- Pokud se domníváte, že entita potřebuje zadat neplatný stav, zvažte použití jiného objektového modelu – například pomocí dočasného objektu DTO, dokud nevytvoříte konečnou entitu domény.

- Pokud potřebujete vytvořit několik souvisejících objektů, jako je například agregace, a jsou platné pouze po vytvoření všech, zvažte použití vzoru Factory.

- Ve většině případů s redundantní ověření na straně klienta je dobré, protože aplikace může být proaktivní.

>[!div class="step-by-step"]
>[Předchozí](domain-model-layer-validations.md)
>[další](domain-events-design-implementation.md)
