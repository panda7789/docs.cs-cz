---
title: 'Postupy: Přidání odkazu na datovou službu (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 8bf623ec74c3bd165f63f60e883bfcb532d6900b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633957"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Postupy: Přidání odkazu na datovou službu (WCF Data Services)

Můžete použít **přidat odkaz na službu** dialogového okna v sadě Visual Studio se přidat odkaz na služeb WCF Data Services. To umožňuje jednodušší přístup ke službě data v klientské aplikaci, která při vývoji v sadě Visual Studio. Po dokončení tohoto postupu datových tříd jsou generovány na základě metadat, která se získá z datové služby. Další informace najdete v tématu [generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

## <a name="add-a-data-service-reference"></a>Přidání odkazu na datovou službu

1. (Volitelné) Pokud datové služby není součástí řešení a není spuštěná, spusťte službu data a poznamenejte si URI datové služby.

2. V sadě Visual Studio v **Průzkumníka řešení**, klikněte pravým tlačítkem na klientský projekt a pak vyberte **přidat** > **odkaz na službu**.

3. Pokud datové služby je součástí aktuálního řešení, klikněte na tlačítko **Discover**.

     -nebo-

     V **adresu** textového pole zadejte základní adresu URL datové služby, jako například `http://localhost:1234/Northwind.svc`a potom klikněte na tlačítko **Přejít**.

4. Vyberte **OK**.

     Do projektu se přidá nový soubor kódu, který obsahuje datových tříd, které můžete používat a komunikovat s prostředkům datové služby.

## <a name="see-also"></a>Viz také:

- [Rychlý start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
