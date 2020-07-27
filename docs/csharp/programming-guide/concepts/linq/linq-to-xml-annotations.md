---
title: Poznámky v LINQ to XML
description: Naučte se používat poznámky v LINQ to XML k přidružení libovolných libovolných objektů libovolného typu k libovolné komponentě XML ve stromu XML.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: e7da666139c10b26de37816693202d96498f52d8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165575"
---
# <a name="linq-to-xml-annotations"></a>Poznámky v LINQ to XML

Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňují přidružit libovolný libovolný objekt libovolného typu k libovolné komponentě XML ve stromu XML.

Chcete-li přidat anotaci do komponenty XML, jako je například <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> , zavoláte <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metodu. Poznámky načtete podle typu.

Všimněte si, že poznámky nejsou součástí informační sady XML. nejsou serializovány nebo deserializovány.

## <a name="methods"></a>Metody

Při práci s poznámkami můžete použít následující metody:

|Metoda|Popis|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Přidá objekt do seznamu poznámek <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Získá první objekt poznámky zadaného typu z <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Získá kolekci poznámek zadaného typu pro <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Odstraní poznámky zadaného typu z <xref:System.Xml.Linq.XObject> .|
