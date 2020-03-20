---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858584"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.ToString(Boolean) nevyvolá nyní, když rozhraní .NET nemůže zpracovat certifikát

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5.2 a starších <code>true</code> verzích by tato metoda vyvolala, pokud by byla předána pro podrobný parametr a byly nainstalovány certifikáty, které nebyly podporovány rozhraním .NET Framework. Nyní metoda bude úspěšné a vrátí platný řetězec, který vynechá nepřístupné části certifikátu.|
|Návrh|Jakýkoli kód <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> v závislosti na by měl být aktualizován očekávat, že vrácený řetězec může vyloučit některá data certifikátu (například veřejný klíč, soukromý klíč a rozšíření) v některých případech, ve kterých by rozhraní API dříve vyvolána.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
