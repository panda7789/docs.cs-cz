---
ms.openlocfilehash: d48519443aeee05617538cf2cc12bea49ad3e16d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761277"
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

