### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Katalogy MEF implementují rozhraní IEnumerable a proto již lze vytvořit serializátor

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, katalogy MEF implementovat rozhraní IEnumerable a proto již lze vytvořit serializátor (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> objekt). Při pokusu o serializaci katalogu MEF vyvolá výjimku.|
|Návrh|MEF lze vytvořit serializátor již nebudete používat|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Modul runtime|

