---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664428"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.ToString(Boolean) nevyvolá nyní při .NET nemůže zpracovat certifikát

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5.2 a dřívějších verzích, tato metoda vyvolá-li <code>true</code> byla předána parametru verbose nebyly nainstalovány certifikáty, které nejsou podporované rozhraním .NET Framework. Metoda teď bude úspěšné a vrátit platný řetězec, který vynechá části nepřístupný certifikátu.|
|Doporučení|Žádný kód v závislosti na <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> očekávat, že vrácený řetězec může vyloučit některé data certifikátu (jako je například veřejný klíč, privátní klíč a rozšíření) v některých případech, ve kterých rozhraní API by mít dříve vyvolána je třeba aktualizovat.|
|Rozsah|Edge|
|Version|4.6|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
