---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379676"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>Xmlschemaexception – správně teď nastavuje pozice řádků

|   |   |
|---|---|
|Podrobnosti|Pokud <xref:System.Xml.Linq.LoadOptions.SetLineInfo> hodnota se předá metodě načíst a dojde k chybě ověření, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> a <xref:System.Xml.Schema.XmlSchemaException.LinePosition> vlastnosti nyní obsahují informace řádku.|
|Doporučení|Kód zpracování výjimek, který předpokládá <xref:System.Xml.Schema.XmlSchemaException.LineNumber> a <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nebude sada by měl aktualizovat, protože tyto vlastnosti budou nyní nastavit správně při použití SetLineInfo při načítání XML.|
|Scope|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
