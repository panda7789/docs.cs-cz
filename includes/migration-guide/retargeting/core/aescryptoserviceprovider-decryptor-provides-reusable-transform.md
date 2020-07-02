---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614444"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Dešifrovací modul AesCryptoServiceProvider poskytuje opakovaně použitelnou transformaci.

#### <a name="details"></a>Podrobnosti

Od aplikací, které cílí na .NET Framework 4.6.2, <xref:System.Security.Cryptography.AesCryptoServiceProvider> dešifrovací modul poskytuje opakovaně použitelnou transformaci. Po volání <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> je transformace znovu inicializována a lze ji znovu použít. Pro aplikace, které cílí na starší verze .NET Framework, se pokusí znovu použít dešifrovací modul voláním <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> po volání metody <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> vyvolá <xref:System.Security.Cryptography.CryptographicException> nebo vytvoří poškozená data.

#### <a name="suggestion"></a>Návrh

Dopad této změny by měl být minimální, protože se jedná o očekávané chování. Aplikace, které závisí na předchozím chování, se můžou z něj odhlásit tím, že do `<runtime>` části konfiguračního souboru aplikace přidají následující nastavení konfigurace:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

Kromě toho aplikace, které cílí na předchozí verzi .NET Framework, ale jsou spuštěné v rámci verze .NET Framework počínaje .NET Framework 4.6.2, můžou se k ní přihlásit přidáním následujícího nastavení konfigurace do `<runtime>` oddílu konfiguračního souboru aplikace:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
