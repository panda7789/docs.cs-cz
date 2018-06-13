---
title: WCF a mezinárodní názvy domén
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: 24b7af660d5fd9629639d3b63d605ef619dcf009
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498033"
---
# <a name="wcf-and-internationalized-domain-names"></a>WCF a mezinárodní názvy domén
Byla přidána podpora pro služby WCF s mezinárodní názvy domén (IDN). Mezinárodní název domény je název domény, který obsahuje jiné znaky než ASCII. Tato podpora zahrnuje možnost k hostování služby WCF s názvu IDN a klienta WCF ke komunikaci s webovou službu pomocí názvu IDN.  
  
## <a name="systemuri-and-idn"></a>System.Uri a IDN.  
 <xref:System.Uri> má dvě vlastnosti <xref:System.Uri.Host%2A> a <xref:System.Uri.DnsSafeHost%2A>. Tyto vlastnosti obsahovat Unicode nebo Punycode hodnoty v závislosti na nastavení konfigurace IDN.  
  
 V konfiguračním souboru aplikace pomocí následující kód XML je povoleno IDN.  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 \<Idn > element obsahuje povoleno atribut, který můžete nastavit na jedno z následujících hodnot:  
  
1.  "Žádný"  
  
2.  "AllExceptIntranet"  
  
3.  "Vše"  
  
 Pokud je na "Žádný" nastavení IDN žádné převody se provádí Uri.Host nebo Uri.DnsSafeHost. Pokud nastavení IDN nastavená na "Vše", identifikátor uri. Hostitel zůstává kódování Unicode a identifikátoru uri. DnsSafeHost je převede na kódování Punycode. Pokud nastavení IDN nastavená na "AllExceptIntranet", identifikátor uri. DnsSafeHost je převede na kódování Punycode pro internetové adresy a zůstane Unicode adres v podnikové síti. Toto nastavení je důležité pro správný překlad názvů DNS. Poznámka: Toto nastavení nemusí být konfigurované pro Windows 8 a novější verze.  
  
> [!WARNING]
>  Měli byste nikdy pevný kód adresu pomocí kódování Punycode. WCF ji převést vám na základě nastavení konfigurace, které použijete.  
  
> [!WARNING]
>  Při přidávání znaky Unicode do applicationHost.exe.config, uložte soubor pomocí kódování UTF-8.  
  
## <a name="see-also"></a>Viz také  
 [System.Uri](http://msdn.microsoft.com/library/system.uri.aspx)
