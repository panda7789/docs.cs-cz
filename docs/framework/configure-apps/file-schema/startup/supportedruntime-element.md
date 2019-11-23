---
title: konfigurační element <supportedRuntime> – .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: 5e7fc5f81468ff7c4eba8145ee42a4c7cf8bc0b8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697523"
---
# <a name="supportedruntime-element"></a>\<element > supportedRuntime

Určuje, která verze modulu Common Language Runtime a volitelně .NET Framework verzi, kterou aplikace podporuje.  

[Konfigurace \<>](../configuration-element.md)  
&nbsp;&nbsp;[\<startup>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<supportedRuntime >**  

## <a name="syntax"></a>Syntaxe

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|**version**|Nepovinný atribut.<br /><br /> Hodnota řetězce, která určuje verzi modulu Common Language Runtime (CLR), který aplikace podporuje. Platné hodnoty atributu `version` naleznete v části ["běhové hodnoty" verze](#version) . **Poznámka:**  V rámci .NET Framework 3,5 má hodnota "*běhová verze*" formu *hlavní*. *vedlejší*. *sestavení*. Počínaje .NET Framework 4 jsou vyžadována pouze čísla hlavní verze a podverze (tj. "v 4.0" místo "v 4.0.30319"). Je doporučen kratší řetězec.|
|**sku**|Nepovinný atribut.<br /><br /> Hodnota řetězce, která určuje skladovou jednotku (SKU), která zase určuje, který .NET Framework vydání této aplikace podporuje.<br /><br /> Počínaje .NET Framework 4,0 se doporučuje použít atribut `sku`.  Pokud je k dispozici, označuje verzi .NET Framework, na kterou aplikace cílí.<br /><br /> Platné hodnoty atributu SKU najdete v části [hodnoty ID SKU](#sku) .|

## <a name="remarks"></a>Poznámky

Pokud **> prvek\<supportedRuntime** není přítomen v konfiguračním souboru aplikace, je použita verze modulu runtime použitého k sestavení aplikace.

Element **\<supportedRuntime >** by měl být používán všemi aplikacemi sestavenými pomocí verze 1,1 nebo novější. Aplikace sestavené pro podporu pouze verze 1,0 modulu runtime musí používat prvek [\<requiredRuntime >](../startup/requiredruntime-element.md) .

> [!NOTE]
> Použijete-li funkci [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) k určení konfiguračního souboru, je nutné použít element `<requiredRuntime>` pro všechny verze modulu runtime. Element `<supportedRuntime>` se při použití [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)ignoruje.  
  
Pro aplikace, které podporují verze modulu runtime od .NET Framework 1,1 do 3,5, je-li podporováno více verzí modulu runtime, první prvek by měl určit nejvíce upřednostňovanou verzi modulu runtime a poslední prvek by měl určovat nejmenší Upřednostňovaná verze. Pro aplikace, které podporují .NET Framework 4,0 nebo novější verze, atribut `version` označuje verzi CLR, která je společná pro .NET Framework 4 a novější verze, a atribut `sku` označuje jednu .NET Framework verzi, na kterou se aplikace zaměřuje. 

Pokud je v konfiguračním souboru přítomen prvek **\<supportedRuntime >** s atributem `sku` a nainstalovaná verze .NET Framework je nižší než zadaná podporovaná verze, aplikace se nespustí a místo toho se zobrazí zpráva s výzvou k instalaci podporované verze. V opačném případě se aplikace pokusí běžet na jakékoli nainstalované verzi, ale může se neočekávaně chovat, pokud není plně kompatibilní s touto verzí. (Kvůli rozdílům kompatibility mezi verzemi .NET Framework, přečtěte si téma [Kompatibilita aplikací v .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Proto doporučujeme, abyste tento prvek zahrnuli do konfiguračního souboru aplikace pro snazší diagnostiku chyb. (Konfigurační soubor, který se automaticky vygeneroval v rámci sady Visual Studio při vytváření nového projektu, ho už obsahuje.)
  
> [!NOTE]
> Pokud vaše aplikace používá starší aktivační cesty, jako je [funkce CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete, aby tyto cesty aktivovaly verzi 4 CLR namísto dřívější verze, nebo pokud je vaše aplikace sestavená s .NET Framework 4, ale má závislost na sestavení se smíšeným režimem vytvořeným pomocí dřívější verze .NET Framework, není dostačující zadat .NET Framework 4 v seznamu podporovaných modulů runtime. Kromě toho je třeba v [\<spuštění > elementu](../startup/startup-element.md) v konfiguračním souboru nastavit atribut `useLegacyV2RuntimeActivationPolicy` na `true`. Nicméně nastavením tohoto atributu na `true` znamená, že všechny komponenty sestavené s dřívějšími verzemi .NET Framework jsou spouštěny pomocí .NET Framework 4 namísto modulu runtime, ve kterém byly vytvořeny.

Doporučujeme aplikaci otestovat se všemi verzemi .NET Framework, na kterých by měla být spuštěna.

<a name="version"></a> 
## <a name="runtime-version-values"></a>hodnoty "verze modulu runtime"
Atribut `runtime` určuje verzi modulu CLR (Common Language Runtime), která je požadována pro danou aplikaci. Všimněte si, že všechny verze .NET Framework v4. x určují `v4.0` CLR. V následující tabulce jsou uvedeny platné hodnoty pro hodnotu *běhové verze* atributu `version`.

|Verze rozhraní .NET Framework|atribut `version`|
|----------------------------|-------------------------|
|1.0|"v 1.0.3705"|
|1.1|"v1.1.4322"|
|2.0|"v 2.0.50727"|
|3,0|"v 2.0.50727"|
|3,5|"v 2.0.50727"|
|4.0 – 4.8|"v 4.0"|

## <a name="sku"></a>hodnoty "ID SKU"

Atribut `sku` používá moniker cílového rozhraní (TFM) k označení verze .NET Framework, na kterou aplikace cílí a kterou vyžaduje spuštění. V následující tabulce jsou uvedeny platné hodnoty, které jsou podporovány atributem `sku` počínaje .NET Framework 4.

|Verze rozhraní .NET Framework|atribut `sku`|
|----------------------------|---------------------|
|4.0|". NETFramework, verze = v 4.0|
|4,0, profil klienta|". NETFramework, verze = v 4.0, Profile = klient|
|4,0, aktualizace platformy 1|". NETFramework, verze = v 4.0.1 "|
|4,0, profil klienta, aktualizace 1|". NETFramework, verze = v 4.0.1, Profile = klient "|
|4,0, platforma Update 2|". NETFramework, verze = v 4.0.2 "|
|4,0, profil klienta, aktualizace 2|". NETFramework, verze = v 4.0.2, Profile = klient "|
|4,0, platforma Update 3|". NETFramework, verze = v 4.0.3 "|
|4,0, profil klienta, aktualizace 3|". NETFramework, verze = v 4.0.3, Profile = klient "|
|4,5|". NETFramework, verze = v 4.5|
|4.5.1|". NETFramework, verze = v 4.5.1|
|4.5.2|". NETFramework, verze = v 4.5.2 "|
|4.6|". NETFramework, verze = v 4.6 "|
|4.6.1|". NETFramework, verze = v 4.6.1|
|4.6.2|". NETFramework, verze = v 4.6.2 "|
|4.7|". NETFramework, verze = v 4.7|
|4.7.1|". NETFramework, verze = v 4.7.1 "|
|4.7.2|". NETFramework, verze = v 4.7.2 "|
|4.8|". NETFramework, verze = v 4.8|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zadat podporovanou verzi modulu runtime v konfiguračním souboru. Konfigurační soubor označuje, že se aplikace zaměřuje na .NET Framework 4,7.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace.

## <a name="see-also"></a>Viz také:

- [Schéma nastavení spouštění](../startup/index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Vnitroprocesové souběžné provádění](../../../deployment/in-process-side-by-side-execution.md)
