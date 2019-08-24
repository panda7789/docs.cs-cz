---
title: WCF a mezinárodní názvy domén
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: 1db62f3e7d073fd1bf9bf9d4d0e17703310f2e69
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988586"
---
# <a name="wcf-and-internationalized-domain-names"></a>WCF a mezinárodní názvy domén
Přidala se podpora, aby služba WCF mohla používat mezinárodní názvy domén (IDN). Mezinárodní název domény je název domény, který obsahuje jiné znaky než ASCII. Tato podpora zahrnuje možnost hostování služby WCF s názvem IDN a klientem WCF pro komunikaci s webovou službou s názvem IDN.  
  
## <a name="systemuri-and-idn"></a>System. URI a IDN  
 <xref:System.Uri>má dvě vlastnosti <xref:System.Uri.Host%2A> a <xref:System.Uri.DnsSafeHost%2A>. Tyto vlastnosti obsahují hodnoty Unicode nebo Punycode v závislosti na nastavení konfigurace IDN.  
  
 V konfiguračním souboru aplikace je povoleno IDN s použitím následujícího kódu XML.  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 Element \<IDN > obsahuje atribut Enabled, který může být nastaven na jednu z následujících hodnot:  
  
1. "None"  
  
2. "AllExceptIntranet"  
  
3. Všem  
  
 Pokud je nastavení IDN nastaveno na hodnotu žádné, neprovede se převody pomocí identifikátoru URI. Host nebo URI. DnsSafeHost. Pokud je nastavení IDN nastaveno na hodnotu "vše", identifikátor URI. Hostitel zůstává v kódu Unicode a v identifikátoru URI. DnsSafeHost se převede na Punycode. Pokud je nastavení IDN nastaveno na hodnotu "AllExceptIntranet", identifikátor URI. DnsSafeHost se převede na Punycode pro internetové adresy a zůstane Unicode pro intranetové adresy. Toto nastavení je důležité pro správné rozlišení názvů DNS. Poznámka: Toto nastavení není nutné konfigurovat pro systém Windows 8 a novější verze.  
  
> [!WARNING]
> Adresu byste nikdy neměli pevně zakódovat pomocí Punycode. WCF je převede na základě nastavení konfigurace, které použijete.  
  
> [!WARNING]
> Při přidávání znaků Unicode do souboru applicationHost. exe. config uložte soubor pomocí kódování UTF-8.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Uri?displayProperty=nameWithType>
