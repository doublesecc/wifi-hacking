# wifi-hacking

## Generating wordlists
### Using cURL

Forward and reverse dictionary searches for related words to given keyword and save to files:
```
keyword='REPLACEME';curl https://relatedwords.org/relatedto/$keyword | grep 'type="text/json"' | cut -f 2 -d '>' | cut -f 1 -d '<' | jq -r '.terms[].word' | tr ' ' '-' > standard_$keyword.txt && \
curl https://reversedictionary.org/wordsfor/$keyword | grep 'type="text/json"' | cut -f 2 -d '>' | cut -f 1 -d '<' | jq -r '.terms[].word' | tr ' ' '-' >> reverse_$keyword.txt && \
cat standard_$keyword.txt reverse_$keyword.txt | sort -u > $keyword.txt
```

### Using ceWL
[ceWL repo](https://github.com/digininja/CeWL)

Crawl website for words and save output to file:
```
cewl --ua "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:109.0) Gecko/20100101 Firefox/117.0" --write <output_file> --depth 3 --lowercase <url> 
```

### Using bopscrk
[bopscrk repo](https://github.com/r3nt0n/bopscrk)

Non interactive wordlist generation based on keywords:
```
python bopscrk.py -m 8 -M 12 -c -l -n 3 -w 2024,wifi,summer -o bopscrk_<output_file>
```

