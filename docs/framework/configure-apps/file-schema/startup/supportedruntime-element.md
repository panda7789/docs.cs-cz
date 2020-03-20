---
title: <supportedRuntime>konfigurační prvek - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: e16eb098db4bce115a5f1e043829eb272c952860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153695"
---
# <a name="supportedruntime-element"></a>\<podporovaný prvek> Runtime

Určuje, kterou verzi za běhu běžného jazyka a volitelně verzi rozhraní .NET Framework aplikace podporuje.  

[\<>konfigurace](../configuration-element.md)  
&nbsp;&nbsp;[\<>pro spuštění](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<podporované>modulu Runtime**  

## <a name="syntax"></a>Syntaxe

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|**Verze**|Nepovinný atribut.<br /><br /> Hodnota řetězce, která určuje verzi modulu Common Language Runtime (CLR), který aplikace podporuje. Platné hodnoty atributu `version` naleznete v části hodnoty [runtime verze.](#version) **Poznámka:**  Prostřednictvím rozhraní .NET Framework 3.5 má hodnota "*runtime version*" *hlavní*formu . *nezletilá*. *stavět*. Počínaje rozhraním .NET Framework 4 jsou vyžadována pouze hlavní a dílčí čísla verzí (tj. "v4.0" namísto "v4.0.30319"). Je doporučen kratší řetězec.|
|**Sku**|Nepovinný atribut.<br /><br /> Hodnota řetězce, která určuje skladovou jednotku (SKU), která zase určuje, kterou verzi rozhraní .NET Framework tato aplikace podporuje.<br /><br /> Počínaje rozhraním .NET Framework 4.0 `sku` se doporučuje použít atribut.  Pokud je k dispozici, označuje verzi rozhraní .NET Framework, na kterou se aplikace zaměřuje.<br /><br /> Platné hodnoty atributu sku naleznete v části [hodnoty sku id.](#sku)|

## <a name="remarks"></a>Poznámky

Pokud ** \<v** konfiguračním souboru aplikace není přítomen prvek supportedRuntime>, použije se verze modulu runtime použitého k sestavení aplikace.

Prvek ** \<supportedRuntime>** by měl být používán všemi aplikacemi vytvořenými pomocí verze 1.1 nebo novější modulu runtime. Aplikace vytvořené pro podporu pouze verze 1.0 runtime musí používat [ \<prvek requiredRuntime>.](../startup/requiredruntime-element.md)

> [!NOTE]
> Pokud k určení konfiguračního souboru použijete funkci [CorBindToRuntimeByCfg,](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) musíte použít `<requiredRuntime>` prvek pro všechny verze runtime. Prvek `<supportedRuntime>` je ignorovánpři použití [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Pro aplikace, které podporují verze modulu runtime z rozhraní .NET Framework 1.1 až 3.5, pokud je podporováno více verzí modulu runtime, první prvek by měl určit nejvíce upřednostňovanou verzi modulu runtime a poslední prvek by měl určit nejméně upřednostňovanou verzi. U aplikací, které podporují rozhraní .NET Framework 4.0 nebo novější verze, `version` atribut označuje verzi CLR, která je `sku` společná pro rozhraní .NET Framework 4 a novější verze, a atribut označuje jedinou verzi rozhraní .NET Framework, na kterou se aplikace zaměřuje.

Pokud je v konfiguračním `sku` souboru přítomen prvek ** \<supportedRuntime>** s atributem a nainstalovaná verze rozhraní .NET Framework je nižší než zadaná podporovaná verze, aplikace se nespustí a místo toho zobrazí zprávu s žádostí o instalaci podporované verze. V opačném případě se aplikace pokusí spustit v libovolné nainstalované verzi, ale může se chovat neočekávaně, pokud není plně kompatibilní s tou verzí. (Rozdíly v kompatibilitě mezi verzemi rozhraní .NET Framework naleznete v tématu [Kompatibilita aplikací v rozhraní .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Proto doporučujeme zahrnout tento prvek do konfiguračního souboru aplikace pro snadnější diagnostiku chyb. (Konfigurační soubor automaticky generovaný visual studio při vytváření nového projektu již obsahuje.)
  
> [!NOTE]
> Pokud vaše aplikace používá starší aktivační cesty, jako je například [funkce CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)a chcete, aby tyto cesty aktivovaly verzi 4 CLR namísto starší verze, nebo pokud je aplikace vytvořena s rozhraním .NET Framework 4, ale má závislost na sestavení ve smíšeném režimu vytvořeném se starší verzí rozhraní .NET Framework, nestačí zadat rozhraní .NET Framework 4 v seznamu podporovaných modulů runtime. Kromě toho je v [ \<spouštěcím prvku>](../startup/startup-element.md) v `useLegacyV2RuntimeActivationPolicy` konfiguračním souboru nutné nastavit atribut na `true`. Nastavení tohoto atributu `true` však znamená, že všechny součásti vytvořené s dřívějšími verzemi rozhraní .NET Framework jsou spouštěny pomocí rozhraní .NET Framework 4 namísto runtimesů, se kterými byly vytvořeny.

Doporučujeme aplikaci otestovat se všemi verzemi .NET Framework, na kterých by měla být spuštěna.

<a name="version"></a>
## <a name="runtime-version-values"></a>hodnoty "runtime verze"
Atribut `runtime` určuje verzi CLR (Common Language Runtime), která je vyžadována pro danou aplikaci. Všimněte si, že všechny verze rozhraní `v4.0` .NET Framework v4.x určují clr. V následující tabulce jsou uvedeny platné hodnoty `version` pro hodnotu *runtime verze* atributu.

|Verze rozhraní .NET Framework|Atribut `version`|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2.0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3,5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku-id-values"></a><a name="sku"></a>hodnoty "sku id"

Atribut `sku` používá zástupný název cílového rozhraní (TFM) k označení verze rozhraní .NET Framework, na kterou se aplikace zaměřuje a která vyžaduje spuštění. V následující tabulce jsou uvedeny `sku` platné hodnoty podporované atributem, počínaje rozhraním .NET Framework 4.

|Verze rozhraní .NET Framework|Atribut `sku`|
|----------------------------|---------------------|
|4.0|". NETFramework,Version=v4.0"|
|4.0, Profil klienta|". NETFramework,Version=v4.0,Profil=Klient"|
|4.0, aktualizace platformy 1|". NETFramework,Version=v4.0.1"|
|4.0, Profil klienta, aktualizace 1|". NETFramework,Version=v4.0.1,Profil=Klient"|
|4.0, aktualizace platformy 2|". NETFramework,Version=v4.0.2"|
|4.0, Profil klienta, aktualizace 2|". NETFramework,Version=v4.0.2,Profil=Klient"|
|4.0, aktualizace platformy 3|". NETFramework,Version=v4.0.3"|
|4.0, Profil klienta, aktualizace 3|". NETFramework,Version=v4.0.3,Profil=Klient"|
|4.5|". NETFramework,Version=v4.5"|
|4.5.1|". NETFramework,Version=v4.5.1"|
|4.5.2|". NETFramework,Version=v4.5.2"|
|4.6|". NETFramework,Version=v4.6"|
|4.6.1|". NETFramework,Version=v4.6.1"|
|4.6.2|". NETFramework,Version=v4.6.2"|
|4.7|". NETFramework,Version=v4.7"|
|4.7.1|". NETFramework,Version=v4.7.1"|
|4.7.2|". NETFramework,Version=v4.7.2"|
|4.8|". NETFramework,Version=v4.8"|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zadat podporovanou verzi modulu runtime v konfiguračním souboru. Konfigurační soubor označuje, že aplikace cílí na rozhraní .NET Framework 4.7.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace.

## <a name="see-also"></a>Viz také

- [Schéma nastavení spouštění](../startup/index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Vnitroprocesové souběžné provádění](../../../deployment/in-process-side-by-side-execution.md)
