---
title: Linq na poznámky XML3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 5f1940be2fc126ff9e9c7a4cb37e5cc7fc95d3c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66689941"
---
# <a name="linq-to-xml-annotations"></a>Poznámky v LINQ to XML

Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aplikaci umožňují přidružit libovolný objekt libovolného typu k libovolné součásti XML ve stromu XML.

Chcete-li přidat poznámku k součásti <xref:System.Xml.Linq.XElement> XML, například nebo <xref:System.Xml.Linq.XAttribute>, zavolejte metodu. <xref:System.Xml.Linq.XObject.AddAnnotation%2A> Poznámky načíst podle typu.

Všimněte si, že poznámky nejsou součástí informační sady XML; nejsou serializovány nebo deserializovány.

## <a name="methods"></a>Metody

Při práci s poznámkami můžete použít následující metody:

|Metoda|Popis|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Přidá objekt do seznamu poznámk <xref:System.Xml.Linq.XObject>y .|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Získá první objekt poznámky zadaného typu <xref:System.Xml.Linq.XObject>z .|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Získá kolekci poznámky zadaného typu pro <xref:System.Xml.Linq.XObject>.|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Odebere poznámky zadaného typu z <xref:System.Xml.Linq.XObject>.|
