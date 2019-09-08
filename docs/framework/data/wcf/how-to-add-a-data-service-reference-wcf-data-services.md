---
title: 'Postupy: Přidání odkazu na datovou službu (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790748"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Postupy: Přidání odkazu na datovou službu (WCF Data Services)

Pomocí dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio můžete přidat odkaz na WCF Data Services. To umožňuje snazší přístup k datové službě v klientské aplikaci, kterou vyvíjíte v aplikaci Visual Studio. Po dokončení tohoto postupu se datové třídy generují na základě metadat získaných z datové služby. Další informace najdete v tématu [generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md).

## <a name="add-a-data-service-reference"></a>Přidat odkaz na datovou službu

1. Volitelné Pokud datová služba není součástí řešení a ještě není spuštěná, spusťte datovou službu a poznamenejte si identifikátor URI datové služby.

2. V aplikaci Visual Studio klikněte v **Průzkumník řešení**pravým tlačítkem myši na projekt klienta a vyberte možnost **Přidat** > odkaz na**službu**.

3. Pokud je datová služba součástí aktuálního řešení, klikněte na tlačítko **zjistit**.

     -nebo-

     Do textového pole **adresa** zadejte základní adresu URL datové služby, například `http://localhost:1234/Northwind.svc`a potom klikněte na tlačítko **Přejít**.

4. Vyberte **OK**.

     Do projektu se přidá nový soubor kódu, který obsahuje datové třídy, které mají přístup k prostředkům datové služby a budou s nimi pracovat.

## <a name="see-also"></a>Viz také:

- [Rychlý start](quickstart-wcf-data-services.md)
