Data source: https://data.ecb.europa.eu/data/datasets/EXR/EXR.D.USD.EUR.SP00.A

Export as CSV

Then convert ist with a command like this e.g. for year 2025 here, if you need another year, change the number under `startswith`:
cat ~/Downloads/ECB\ Data\ Portal_20260121114940.csv | csv2json | jq '[ .[] | select(.DATE | startswith("2025-")) | .DATE |= (split("-") | "\(.[1])/\(.[2])/\(.[0])") ]' | jq 'map({(.DATE): ."US dollar/Euro (EXR.D.USD.EUR.SP00.A)" | tonumber }) | add'
