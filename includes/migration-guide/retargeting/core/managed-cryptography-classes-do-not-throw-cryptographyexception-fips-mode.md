---
ms.openlocfilehash: 0b62eff8d70873293aafa539f40bf032672df57a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617801"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a>Spravované kryptografické třídy nevyvolávají výjimku CryptographyException v režimu FIPS.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.7.2 a starších verzích spravované třídy zprostředkovatele kryptografických služeb, jako je například <xref:System.Security.Cryptography.SHA256Managed> vyvolat a v <xref:System.Security.Cryptography.CryptographicException> případě, že systémové šifrovací knihovny jsou konfigurovány v režimu FIPS. Tyto výjimky jsou vyvolány, protože spravované verze neprošly certifikací FIPS (Federal Information Processing Standards) 140-2 a také k blokování kryptografických algoritmů, které nebyly považovány za schválené na základě pravidel FIPS.  Vzhledem k tomu, že někteří vývojáři mají své vývojové počítače v režimu FIPS, jsou tyto výjimky často vyvolány pouze v produkčních systémech. Aplikace, které cílí na .NET Framework 4,8 a novější verze, automaticky přepnou na novější, uvolněnou zásadu, takže <xref:System.Security.Cryptography.CryptographicException> v takových případech již není vyvoláno ve výchozím nastavení. Místo toho spravované kryptografické třídy přesměrují kryptografické operace do systémové knihovny kryptografie. Tato změna zásad efektivně odstraňuje potenciálně matoucí rozdíl mezi vývojářskými prostředími a provozními prostředími a zpřístupňuje nativní komponenty a spravované komponenty v rámci stejných kryptografických zásad.

#### <a name="suggestion"></a>Návrh

Pokud je toto chování nežádoucí, můžete si ho odhlásit a obnovit předchozí chování tak, aby <xref:System.Security.Cryptography.CryptographicException> byl v režimu FIPS vyvolán přidáním následujícího nastavení konfigurace [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=true" />
</runtime>
```

Pokud je vaše aplikace cílena .NET Framework 4.7.2 nebo starší, můžete k této změně také vyjádřit přidáním následujícího nastavení konfigurace [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4,8         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType>
