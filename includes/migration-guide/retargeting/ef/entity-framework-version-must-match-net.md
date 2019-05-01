---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088478"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Entity Framework verze musí odpovídat verzi rozhraní .NET Framework

|   |   |
|---|---|
|Podrobnosti|S verzí rozhraní .NET framework by si měly odpovídat verzi rozhraní entity framework. Entity Framework 5 se doporučuje pro rozhraní .NET Framework 4.5. Existují některé známé problémy s platformou EF s 4.x v projektu rozhraní .NET Framework 4.5 kolem <xref:System.ComponentModel.DataAnnotations>. V rozhraní .NET 4.5 tyto se přesunuly na jiné sestavení, takže dojde k problémům určující, které poznámky k použití.|
|Doporučení|Upgrade na rozhraní Entity Framework 5 pro rozhraní .NET Framework 4.5|
|Rozsah|Hlavní|
|Version|4.5|
|Type|Změna cílení|
