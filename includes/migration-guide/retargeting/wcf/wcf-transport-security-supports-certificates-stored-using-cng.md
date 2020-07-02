---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614500"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>Zabezpečení přenosu WCF podporuje certifikáty uložené pomocí CNG

#### <a name="details"></a>Podrobnosti

Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, podporuje zabezpečení přenosu WCF certifikáty uložené pomocí knihovny kryptografických služeb systému Windows (CNG). Tato podpora je omezená na certifikáty s veřejným klíčem, který má exponent větší než 32 bitů. Když je aplikace cílena na .NET Framework 4.6.2, je tato funkce ve výchozím nastavení zapnutá. V dřívějších verzích .NET Framework se pokus o použití certifikátů x509 s poskytovatelem úložiště klíčů CSG vyvolá výjimku.

#### <a name="suggestion"></a>Návrh

Aplikace, které cílí na .NET Framework 4.6.1 a starší, ale běží na .NET Framework 4.6.2, můžou povolit podporu pro certifikáty CNG přidáním následujícího řádku do `<runtime>` oddílu souboru app.config nebo web.config:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

To lze provést také programově pomocí následujícího kódu:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

Všimněte si, že vzhledem k tomu, že v důsledku této změny, nebude již spuštěn žádný kód pro zpracování výjimek, který závisí na pokusu o zahájení zabezpečené komunikace s certifikátem CNG na selhání.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6.2       |
| Typ    | Změna cílení |
